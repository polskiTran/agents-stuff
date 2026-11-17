# Traps

Each trap has the same three parts: what it looks like in a result, how it happens, and the check that catches it. The check goes into the analysis script, with its counts in the log.

## Joins

### Fan-out

**Looks like:** a total that is larger than the source system reports, or a count of customers larger than the customer table.

**How:** the join key is not unique on the side you assumed it was. Each duplicate multiplies the rows on the other side.

**Check:** assert the key is unique on the "one" side before the join. Compare the row count and the sum of the main measure before and after. A many-to-one join keeps the row count of the many side.

### Silent loss

**Looks like:** a rate that is better than expected, or a segment that shrank for no reason.

**How:** an inner join drops rows that have no match, and the unmatched rows are rarely random. Flights with no aircraft record, orders from deleted accounts, events from an old app version.

**Check:** count the rows with no match (an anti-join) and compare their outcome with the matched rows. When they differ, the join is selecting.

### False match

**Looks like:** nothing, in the totals. Row counts and sums are unchanged by the join, and every key matched.

**How:** the key matches a record for a different entity. Ids get reused, or one system stores a fleet or internal number where the other expects a registration. A flight joins to a light aircraft or a helicopter, a customer joins to someone else's account.

**Check:** after the join, compare attributes from both sides that must agree: an airline flight needs an airliner, an order total needs a plausible customer country. List the matched records that fail, and count their rows.

## Grain and time

### Wrong grain

**Looks like:** counts that are a small multiple too high, or averages pulled toward entities with many rows.

**How:** the table holds one row per line, version or event, and the question needs one row per order, customer or session.

**Check:** assert uniqueness at the question's grain. Count distinct entities beside the row count.

### History rewritten

**Looks like:** last quarter's number changes each time you rerun it.

**How:** a current-state table overwrites old values when a status changes. A history table keeps one row per version, and the analysis takes the wrong one.

**Check:** filter versions to the state as of the time the question asks about. Log the as-of rule in Decisions.

### Partial period

**Looks like:** a sharp drop in the latest period.

**How:** the last period has not ended, or late data has not arrived yet.

**Check:** count rows per period and per day inside the last period. Measure the lag between event time and load time, and cut the window where data is complete.

### Timezone and day boundary

**Looks like:** daily totals that disagree with another report by a few percent, or a spike at midnight.

**How:** sources store times in different zones, or bucket days with different cutoffs.

**Check:** convert every timestamp to one zone before bucketing, and log which zone. When a table carries both local and UTC fields, check that they agree. Compare one day's total with the other report.

### Clock arithmetic

**Looks like:** a few durations that are hugely negative or close to a full day.

**How:** times are stored as clock numbers (`930` for 09:30) or as local times without a date, and an event crosses midnight. Subtracting the numbers gives the wrong duration.

**Check:** build full timestamps from date and time before subtracting. Count events whose end is earlier in the clock than their start, and read some of them.

## Values

### Placeholder values

**Looks like:** a spike at one value, such as 0, -1, 999, 1900-01-01 or 1970-01-01, or many rows that say "unknown".

**How:** a system writes a default when the real value is missing.

**Check:** list the most frequent values of each column the question uses, and treat each placeholder as missing.

### Missing not at random

**Looks like:** the average of a measure improves after rows with nulls are dropped.

**How:** the null marks a specific case. A cancelled flight has no arrival delay, so dropping null delays drops the worst trips.

**Check:** compare the null rate across segments and across the outcome-related columns. When it varies, model the missing rows as a separate case, never as noise.

### Duplicates and test traffic

**Looks like:** round bursts of activity, or a few accounts with impossible volumes.

**How:** clients retry and log one event twice. Internal and test accounts sit in production tables.

**Check:** count rows that are identical apart from their load id or timestamp. Look up how the source marks test and internal accounts, and exclude them in code.

## Definitions and populations

### Denominator drift

**Looks like:** a rate that moves at a date when nothing happened to the product.

**How:** the definition of eligible, active or a session changed during the window, or logging changed.

**Check:** plot the numerator and the denominator separately over time. Ask the data's owner about definition and logging changes in the window, and log the dates.

### Survivors only

**Looks like:** customers look healthier the further back the analysis goes.

**How:** churned, failed or hard-deleted entities are missing from the table, so the past holds only the ones that lasted.

**Check:** compare the count of entities that started in each period with an independent record of starts, such as signups or invoices.

### Selection on the outcome

**Looks like:** a segment with a striking outcome, such as "users who finished onboarding retain twice as well".

**How:** the segment is defined by behavior that is part of the outcome, or caused by it.

**Check:** define segments only from what was known before the outcome period started.

### Mix shift

**Looks like:** the total rate rises while the rate falls in every segment, or the reverse.

**How:** the share of a high-rate segment grew. This is Simpson's paradox.

**Check:** compute the rate per segment beside the total, and the segment shares per period. Report both.

## The tooling itself

### Pipeline bias

**Looks like:** results that lean one way across many unrelated analyses.

**How:** the assignment, logging or metric code has a bug that shifts every result.

**Check:** run the pipeline on input where the answer is known. For experiments, that is an A/A test, where both groups get the same treatment. [Experiments at Airbnb](https://medium.com/airbnb-engineering/experiments-at-airbnb-e2db3abf39e7) (Overgoor, 2014) reports dummy runs with evenly split groups that came back neutral, and runs with uneven splits that showed a large bias against the treatment group. The team found several bugs in its own system this way.
