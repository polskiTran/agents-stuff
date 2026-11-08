# dara's agents.md (excerpt)
- category: coding
- post link: https://x.com/daradoescode/status/2082696597528592594
- description: An excerpt of @daradoescode's AGENTS.md for the Weaver widget framework: named concepts (landmine, receipt, tripwire, simple, obvious) and build philosophies. Her linked X article walks through how she wrote it.

## prompt

```text
weaver sdk - the actual widget runtime/entire stack

And the words we use when we work:

landmine - a decision that costs nothing now and blows up later. by the time it detonates it's load-bearing. (i.e. an unmeasured limit, a silent catch)
receipt - the measurement behind a number. no receipt, no number.
tripwire - a limit placed past where any good widget goes, so only broken things touch it. good widgets never feel it exists.
simple - how cleanly the logic breaks down. each step follows from the last, no step doing two jobs.
obvious - the next reader never asks "why is this here?". measured by the reader. not always simple; sometimes obvious has more parts.

Here's some philosophical things to consider as we build and work together

## Boil the ocean
When planning, do not be afraid to suggest seemingly insane solutions. we effectively have to rethink and rebuilt the what it means to make a desk widget platform. It needs to be cross platform while having a amazing developer experience. The syntax should resemble tsx/jsx, so developers/agents(who are familiar with the web) are able to transition easily. We want the efficiency to be super high with memory and cpu usage being as low as possible, yet still keeping that amazing dev ex.

## Every number needs a receipt
A limit without a measurement is a landmine. Before writing any number (a `max_nodes`, a byte cap, a timeout), measure the real thing first, then size it as a tripwire. Capacity is free until touched (reserve big, commit lazily, never zero an arena eagerly), so be generous. If a good widget hits a budget, the budget is wrong. Remeasure, update the receipt.

## A limit developers can hit is a limit they must see
Developers won't read our code. Their agents read our errors. An agent can fix "max_nodes=128, asked for 129". It cannot fix a blank window. Every budget failure names the budget, the limit, and the ask: at `weaver check` if knowable there, loudly at runtime if not. A silent budget is worse than no budget.

## Fight for the "obvious" solution
Measure twice, cut once: understand the problem fully before building, because cleverness is what gets written when you haven't. The biggest simplicity win is refusing to solve problems we don't have. Good code is the most simple thing that delivers full functionality and performance, nothing traded away, nothing bolted on. Push back when you see a more obvious way.
```

edits: transcribed from the post image, which shows only lines 10–32 of the file (the start and end aren't visible); dropped the line numbers and joined the wrapped lines. The author's typos are kept.
