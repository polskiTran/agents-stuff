# Document types

Each section gives the page order for one type, the moves it leans on, and the traps that type falls into. Move numbers refer to [moves.md](moves.md). Every type still gets every step in [SKILL.md](SKILL.md).

## Decision memo

One page. The reader has a choice to make and little time.

**Page order**

1. Title that states the recommendation.
2. Recommendation and confidence label, in two or three sentences.
3. The decision: what is being chosen, by whom, by when.
4. Two to four findings, each under a title that states its lesson.
5. Residual risk and what would change the conclusion.
6. Methods block, as a box at the end.
7. Link to the full analysis.

**Leans on** moves 1, 7, 8 and 10.

**Traps**

- Telling the story of the analysis in the order it happened. The reader wants the answer first.
- A recommendation with no stated risk.
- More than four findings. Move the rest to the linked analysis.

Eugene Yan's [Why, What, How framework](https://eugeneyan.com/writing/writing-docs-why-what-how/) describes what a one-pager must let a reader grasp quickly: the problem, the expected outcome, the proposed solution and the approach. It has worked examples of a one-pager and an after-action review.

## Experiment readout

The reader wants to know whether to ship.

**Page order**

1. Title that states the result and the decision.
2. Summary: ship, do not ship, or extend the test, with the effect on the primary metric and its interval.
3. Hypothesis: change X will improve the experience in a way that moves metric Y.
4. Decision rule as set before the test: primary metric and threshold, guardrail metrics, secondary metrics.
5. Health checks: the split between groups matches the design, the test ran for its planned length, and any A/A or dummy run came back neutral.
6. Results, grouped by metric role. Primary first, then guardrails, then secondary.
7. Segments, each marked planned or exploratory.
8. Limitations.
9. Recommendation and residual risk.
10. Methods block.

**Leans on** moves 5, 6 and 8.

**Traps**

- Calling the result at the first moment it crosses significance. Show the metric over the whole test window.
- Reporting only the metrics that moved. Report every metric in the decision rule.
- Randomizing units that share a resource, such as riders who share drivers. One group's treatment then changes the other group's outcome, and the estimate is biased. Name the shared resource under limitations.
- A result that looks too good. Check the system before you report it.

## Methods write-up

The reader wants to rely on the method or repeat it.

**Page order**

1. What the method is for, and its scope.
2. The method in one short definition that a reader can test against their own case.
3. A worked example, start to finish.
4. The choices made and the alternatives rejected, each with its reason.
5. Validation: the method run on a case where the true answer is known.
6. Limitations, and the uses the method is not suited to.
7. How to reproduce it: data, code, versions.

**Leans on** moves 2, 3 and 4.

**Traps**

- Defining a measure after the results that use it. Define each measure, with a small numeric example, before the first result.
- Leaving out the rejected alternatives. The reader will think of them and wonder.
- A limitations section added at the end as an afterthought. Announce it in the introduction.

## Explainer

The reader wants to understand, and holds an intuition that is partly wrong.

**Page order**

1. Title that states the lesson.
2. The default view, stated in a form its holders would accept.
3. Where the default view breaks, shown on the smallest example that breaks it.
4. The build-up: figures that change one thing at a time, under section titles that state lessons.
5. Where the default view is still good enough.
6. Summary of the lessons.

**Leans on** moves 1, 3 and 9.

**Traps**

- Formalism before intuition. Give the picture first and the mechanism second.
- A new example in every section. One running example carries the piece.
- A real, contested example that pulls the reader into arguing about the example. An example that is plainly made up, and flagged as made up, avoids this.

## Survey or insight report

The reader wants to know what a group of people think or do, and how far the numbers can be trusted.

**Page order**

1. Title and subtitle that state the finding and who it holds for.
2. Key findings, with the confidence label.
3. "How we did this" box: n, field dates, the sampling frame or panel and how people were recruited into it, the mode, the weighting variables, and links to the questionnaire and tables.
4. Findings. Each number sits beside the exact wording of its question.
5. Subgroup results, each with its own n, and a caution where the n is small.
6. What the data cannot say: who is missing, and how the recruitment method could bias the answer.
7. Calibrated verdict and recommendation.

**Leans on** moves 4, 5, 7 and 8.

**Traps**

- Paraphrasing a question. Small changes in wording change answers, so quote it.
- A subgroup percentage with no base.
- Reading an opt-in online sample as if it were a random sample. Opt-in samples can go badly wrong for small subgroups and rare attitudes. Say which kind of sample this is.
- Comparing two surveys that differ in wording, mode or sample, and calling the gap a change in opinion.

**Coverage.** This section is built on published public-opinion survey writing. It has no worked examples for commercial market research readouts: brand trackers, segmentation, conjoint, MaxDiff, concept tests. The page order above still applies to them. Their method-specific reporting is not covered here, so mark those fields `[NEEDS]` and ask the analyst.

## When the document is a list

Some documents are a catalog of pitfalls or a set of lessons from many projects. They can be any of the types above.

- Number the items and title each one as its lesson.
- Give every item the same three parts: a real case that looked puzzling, the mechanism behind it, and how to detect or prevent it.
- Say where the items come from and how many cases stand behind them.
