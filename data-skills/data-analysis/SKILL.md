---
name: data-analysis
description: "Answer a question from data by reading raw rows, turning what you see into checks, and tracing every number to its records. Use when profiling or cleaning a dataset, computing an answer with a query, script or notebook, or chasing a number that looks wrong."
---

# Data analysis

A number from an analysis passed through a source system, a query, joins, filters and a formula before it reached you. Most wrong numbers go wrong on that path, not in the statistics. This skill keeps the path in view.

The core is a loop: **look** at rows, **write down** what you see, turn it into a **check**, **measure** how many rows it touches. Repeat until new looks stop finding new problems.

## Two rules that hold at every step

- **Raw data is read-only.** The answer comes from one script that runs from the raw sources to the answer in one pass, in a fresh environment. Keep edits out of the raw files and out of notebook state you cannot rerun. Scripts you used only to read rows can stay rough, but keep them.
- **A surprise is a bug until rows say otherwise.** When a result is surprising, or exactly what everyone hoped for, find the rows that produce it and read them before you report it.

## The analysis log

Keep one log file beside the code, `analysis-log.md`. Every step writes to it. If your environment cannot write files, return the log as text. Start it with these sections and fill them as you go:

```markdown
## Question
Quantity, definitions, grain, population, window, denominators. Expected range. Planned comparisons.

## Sources
| source | as of | rows | key (verified) | fingerprint |

## Observations
- <row or entity id>: what you saw

## Checks
| check | asserts | failing rows | share of rows | share of measure |

## Row ledger
| step | rows in | rows out | reason |

## Looks
| comparison | planned or exploratory | result | kept? |

## Decisions
| decision | alternative | why | answer if reversed |
```

Write **observations, not explanations**: "order 1182 ships before it was placed", not "the shipping system is buggy". An explanation is a guess, and it closes the question too early.

## Steps

### 1. Pin the question

- Write the question as a quantity you can compute. "Share of Q3 orders refunded within 30 days" can be computed. "How are refunds doing" cannot.
- Turn every vague word in the question into a definition. "Older aircraft" needs an age and a cut point. "Active user" needs an event and a window. These definitions are where an analysis can drift toward the answer it likes, so fix them now, before you compute any outcome.
- Name the **grain** the answer needs (one row per what), the population (which rows count), the window, and the denominator of each rate.
- Write the answer you expect and the range that would surprise you. You are not testing this guess. You are making surprise detectable in step 7.
- List the comparisons you plan. Anything you compute later is exploratory, and the log says so.

**Done when** the log holds the quantity, every definition with its cut points, the grain, population, window, denominators, expected range and planned comparisons.

### 2. Register the sources

For each table or file the analysis uses, log where it lives, the as-of time, the row count, a fingerprint (a file hash, or the latest `updated_at`), and its key. When the as-of time is unknown, say so.

- Confirm the key is unique with a query. A column called `id` is a claim, not a key. When there is no id column, find the smallest set of columns that is unique, and log how many duplicates the next-smaller set has.
- Find the grain the source actually has: one row per order, per order line, per order version, per event.
- When the source grain differs from the question's grain, write the path between them: aggregate, deduplicate, take the latest version, join. Most errors enter on that path.

**Done when** every source used has a fingerprint and a verified key, and the grain path is written down.

### 3. Look at rows

Read raw rows before any summary statistic.

- From each source, read about 40 random rows, all columns.
- Then read the **edges**. Random rows find common problems. Edges find the rare ones, which are often the ones that matter. Read the largest and smallest values of each measure the question uses, the oldest and newest dates, the most frequent value of each id, and rows with nulls in the columns the question uses.
- Read joined rows. After each join, read rows with the attributes from both sides together, and ask whether the matched record can be the right one: an airline flight matched to a helicopter is a key that matched the wrong entity.
- For each oddity, write one observation with its row or entity id. Record the first thing wrong. Later symptoms usually follow from it.
- Find out what a row means in the source system. When is it created, updated, deleted? Does a cancelled order stay with a new status, or disappear? Ask the data's owner when the docs do not say. With no owner to ask, log the question and the assumption you made.
- After about 20 observations, group them into named problem types, each with a one-line definition. Take the names from what you saw ("refunds with no matching order"), not from a generic list ("data quality").

**Done when** a fresh batch of 10 random rows and 10 rows from an edge you have not read yet turns up no new problem type.

### 4. Turn observations into checks

Each problem type, and each assumption the answer rests on, becomes an executable check. The checks run in the same script as the answer and print counts. A check that fails stops the run, or prints a loud warning that the log explains.

Every analysis gets at least these:

- The key is unique at every grain the analysis passes through.
- Row counts before and after every join, with the expected relationship asserted: one to one, or many to one.
- The share of rows with no match in each join, and the outcome of unmatched rows beside matched ones.
- The time coverage of the window: no missing periods, no partial last period, and a known zone for every timestamp.

Then add the checks your observations call for. [traps.md](traps.md) lists common traps, each with the check that catches it. Read it once per analysis, and read a trap's entry again whenever an observation resembles it.

For each check, log three numbers: the failing rows, their share of rows, and their share of the measure. A problem in 0.1% of rows can carry 30% of the revenue. For a measure that can be negative, use the share of its absolute value. When the failing rows have no value for the measure, write "none" and compare those rows with the rest on a related outcome instead.

Count failing rows on the raw data. The row ledger in step 5 counts removals in order, so a row already removed by an earlier step is not counted again. When the two counts differ, say why in the ledger.

**Done when** every problem type and every join has a check with logged counts.

### 5. Clean, with a row ledger

- Make one change at a time, in code. Log each in the row ledger: rows in, rows out, and the reason.
- Flag first, then filter on the flag. A flag keeps each excluded row available for the checks in step 7.
- Decide exclusions by what a row is, never by its outcome value. Dropping the worst outcomes as "outliers" changes the answer to the question.
- Log every judgement call in Decisions, with the alternative you rejected.
- Rerun the checks that apply to the cleaned data: keys, join relationships, ranges and time coverage.

**Done when** the ledger reconciles to the row (the raw count minus every removal equals the final count), and every check passes or has a logged reason it may fail.

### 6. Compute the answer

- Compute from rows at the question's grain. Leave pre-computed averages out of any further averaging.
- Put the numerator, the denominator and the n beside every rate, for each group.
- Give the uncertainty, or say why none applies. A full census of a finite population has no sampling error, but a question about a general pattern ("do older aircraft run later?") still needs an interval.
- When rows repeat for one entity (many flights per aircraft, many sessions per user), resample or cluster by that entity, not by row. Rows from one entity are not independent.
- Log every outcome comparison as a look, including the ones you discard and the segment splits and reversals you run in step 7.

**Done when** the answer has its numerators, denominators, n and uncertainty, and the looks table lists every comparison computed.

### 7. Try to break it

- **Compute it a second way.** Use a different query path or tool, from the raw sources, or an independent total such as a finance report. This checks the code, not the decisions. The two answers agree, or the gap is explained.
- **Trace three entities.** Pick one typical id, one extreme id, and one id flagged in step 5. Follow each by hand from its raw rows to its share of the answer, or to the step that excluded it.
- **Reverse each decision.** Recompute with each judgement call in Decisions reversed, and log how far the answer moves. When the data cannot support the reversal, log why, and compare the excluded rows with the rest on any outcome you do have.
- **Split by the obvious segments**, such as time period and the largest category.
- **When segments and the total disagree**, the total is mixing segments of different size and level. Find which segment drives the mix. Then decide which comparison answers the question as worded: the total describes what happened across the whole population, and the within-segment comparison holds the segment fixed. Lead with that one, report the other beside it, and log the choice in Decisions.
- **Compare with the expected range** from step 1. When the answer falls outside it, go back to step 3 and read the rows that drive the gap.

**Done when** the second way agrees, three entities are traced, every decision has its reversed result or a logged reason it has none, and every surprise has rows behind it.

### 8. Hand off

- Pin the environment with a lock file, and record the one command that reruns the analysis from raw sources to the answer.
- Run that command once in a fresh environment.
- Give a verdict: **ready**, **ready with caveats** (list them), or **not ready** (list what blocks it).
- When the result goes into a document, write it with the `data-writing` skill. Its methods block and its count of looks come from this log.

**Done when** the command reproduces the number in a fresh environment, and the log explains every step between the raw rows and that number.

## Shorter paths

- **One number from a known table:** steps 1, 2 and 6, plus the second way from step 7. Keep the log anyway. It is short.
- **A number that looks wrong:** start at step 3 with the rows behind that number, then run steps 4 and 7.
- **A dataset with no question yet:** steps 2 to 5. The output is the problem types, the checks and the ledger, ready for a question later.

## Sources

The look, write down, measure loop is adapted from Hamel Husain and Shreya Shankar's [`error-analysis`](https://github.com/hamelsmu/evals-skills/tree/main/skills/error-analysis) skill, which applies it to LLM traces. Several checks in [traps.md](traps.md) also appear in the pitfall catalog of Anthropic's [`validate-data`](https://github.com/anthropics/knowledge-work-plugins/tree/main/data/skills/validate-data) skill.
