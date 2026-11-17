---
name: data-writing
description: "Write or review a document that reports data work: an analysis or decision memo, an experiment readout, a methods write-up, an explainer, or a survey and insight report."
---

# Data writing

A data document takes a reader from a question to an answer they can act on, and shows them how far to trust it.

Build the parts of the argument in the order below. That order is not the order on the page. Findings are written sixth, so by then a frame, a methods block and a confidence statement already exist and the findings have to fit inside them.

This skill owns the argument. Sentence style belongs to your general writing skills, which run in step 8.

## Two rules that hold at every step

- **Trace every number.** Each number, quote and source in the document comes from something you read in this session: a query result, a notebook output, a table, a paper. When one is missing, ask the analyst, or write `[NEEDS: what, from whom]` in its place and keep going.
- **Report the analysis that was run.** When the comparison a reader needs was never made, the document says so under limitations. If you are able to run it, propose that to the user first.

## Steps

### 1. Classify the document

| Type | The reader asks |
| --- | --- |
| Decision memo | What should we do? |
| Experiment readout | Did the change work, and do we ship it? |
| Methods write-up | How was this done, and can I rely on it or repeat it? |
| Explainer | How does this work, and where does my intuition fail? |
| Survey or insight report | What do these people think or do, and how sure are we? |

Read that type's section in [document-types.md](document-types.md). It gives the page order and the moves that type leans on.

A document that answers two of these questions is two documents. Write the one the reader will act on, and link the other.

**Done when** you have one type and one named reader. A role is enough: "the pricing lead".

### 2. Frame it

Write four lines:

- **Decision or question.** The choice someone will make, or the question that has an answer, in the reader's words. Leave method names out.
- **Reader.** Who they are, what they believe now, and what they will do with the document.
- **Default view.** The common belief, the naive method, or the current practice that this document tests.
- **Scope.** What the document covers, what it leaves out, and how firm an answer it aims for.

If the user is available, show them the frame before going on. A wrong frame is the most expensive mistake to fix later.

**Done when** the decision line names a choice or an answerable question, the default view is something the reader would agree with today, and the scope line names at least one thing left out.

### 3. Fill in the methods block

The methods block is a compact block that a reader can check without reading the narrative. Fill it before any finding is written. When the analysis kept an `analysis-log.md` (from the `data-analysis` skill), fill the block from its sources, row ledger and decisions, and take the count of looks for step 5 from its looks table.

- **Data.** The source, the population or sampling frame, and how units got into the data.
- **Size and dates.** The n, per group where there are groups, and the collection or test window.
- **Unit.** What one row is. For an experiment, the unit of randomization.
- **Measures.** The exact definition of each metric. For a survey, the exact question wording.
- **Adjustments.** Weighting, filters, exclusions and imputation, with the count each one removed or changed.
- **Analysis.** The model or test, and the comparison it makes.
- **Where to check.** Links to the code, the query, the questionnaire, the tables.

**Done when** every field holds a traced value, or "not applicable" with the reason, or a `[NEEDS]`.

### 4. Plan the evidence

Write these as a short list:

- **The objection.** The first thing a skeptical reader will say: "that is seasonality", "the two groups were different to begin with", "the question was worded differently". Then name the comparison in the analysis that answers it. If no comparison answers it, the objection goes into limitations and you tell the user.
- **The running example.** One concrete case that every section returns to: one customer, one market, one test, one survey question.
- **The known-truth model.** Use it when the document argues that a method is right or wrong. Build the smallest case where the true answer is known by construction, and compute the naive answer beside it. Skip it when the document reports a result and makes no claim about a method.
- **The figures.** List them in order, each with one sentence that says what the figure shows. Each figure makes one comparison. Read the sentences alone, top to bottom: they should make the argument without the prose.

**Done when** the objection has its comparison or its place in limitations, and every figure has its sentence.

### 5. Write the confidence and the caveats

Write these before drafting any finding, so that an attractive result cannot soften them.

- **Confidence label.** One sentence on how settled the answer is, with the reason. "Preliminary: two weeks of data from one market."
- **Caveats.** The conditions a reader needs before they see a number, because the conditions change how the number reads.
- **The looks.** Count the metrics, segments and model specifications that were examined. Say which were fixed before the results were seen. Every finding will be marked planned or exploratory from this list.
- **Limitations.** What the data cannot show, who is missing from it, and what was not tested.
- **What would change the conclusion.** The observation that would reverse the answer.

**Done when** all five exist and the looks have counts.

### 6. Write the findings

- **Title and summary first.** The title states the finding. The summary answers the decision line in two or three sentences, with the key number and its uncertainty.
- **Section titles state lessons.** A reader who reads only the titles gets the argument.
- **Each finding has four parts:** the claim, the number with its interval and its base, the figure, and what the finding means for the decision.
- **Tie the numbers to the decision rule.** Name the primary metric and the threshold set for it, the guardrail metrics that must not get worse, and the secondary metrics that explain why the primary moved. Say whether each condition was met. If no rule was set before the results were seen, say that.
- **Give a calibrated verdict.** Say what held up and what did not. Say where the default view still works. Give null and negative results the same weight as positive ones.
- **Describe mechanisms.** When an earlier method or analysis got the answer wrong, explain how the error arises. The explanation is about the method, and the people who used it acted reasonably.

**Done when** every finding has a number, its uncertainty and its base, and the verdict names at least one result that did not support the main claim, or states that none was found.

### 7. Close

- **Recommendation.** The action and who takes it, as a direct answer to the decision line.
- **Residual risk.** What could still be wrong after this work, and what that would cost.
- **Next check.** What would change the conclusion, from step 5, and the cheapest way to look for it.
- **Invitation.** Where to send corrections, and where the data and code live.

**Done when** a reader who reads only the summary and the close knows what to do and what could go wrong.

### 8. Review

1. Assemble the parts in the page order from [document-types.md](document-types.md).
2. Check the draft against every move in [moves.md](moves.md). For each move write "pass", or "fail" with the place in the draft. Fix each fail, or record why it stays.
3. Trace every number in the draft back to its source. A number in the summary must equal the same number in the body and in the figure.
4. Apply the general writing and prose-cleanup skills you have, such as `technical-writing` and `unslop`.
5. Hand over the draft with the open `[NEEDS]` items and any move that still fails.

**Done when** every move has a recorded result and every number has a source.

## Seeing a move done well

[moves.md](moves.md) links one or more published pieces for each move, with a note on where to look. When you are unsure what a move looks like on the page, read the piece.
