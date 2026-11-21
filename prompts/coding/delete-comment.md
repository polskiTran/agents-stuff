# delete-comment
- category: coding
- post link: https://x.com/mattpocockuk/status/2123798388227403983
- description: @mattpocockuk's prompt that audits every code comment as tautology, excuse, stale or decision record, then deletes or files issues, moves decisions into ADRs, adds a ratcheting lint rule that bans all comments, and creates a /delete-comment skill so the sweep can be repeated.

## prompt

```text
Take a look at every code comment in <my codebase | this section of the code>.

Categorise each comment as:

- Tautology: simply repeats what is already visible from the code
- Excuse: many comments allow the agent to get away with a hacky implementation, which then gets propagated through the code
- Stale: references code or implementation information that is no longer relevant
- Decision Record: documents an important, non-obvious decision about the code

For each comment, take this action:

- Tautology/Stale: delete the comment
- Excuse: delete the comment and file an issue to fix the hacky implementation
- Decision Record: move it into an ADR

Once this is done:

- Create a lint rule banning comments for <my codebase | this section of the code>
- Take a ratchet approach, assuming not all comments will be deleted this PR
- Create a /delete-comment skill in this repository so we can repeat this process later
- Estimate for me how many lines of code we'll shed by deleting all comments
```

edits: kept only the prompt; removed the author's intro line and outro.
