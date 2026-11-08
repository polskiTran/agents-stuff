# e2e-first testing rules
- category: coding
- post link: https://x.com/anshnanda/status/2101627891721371971
- description: AGENTS.md testing rules from @anshnanda: no post-hoc unit tests, prefer E2E tests that produce a verifiable artifact, and list failure modes before writing isolated code.

## prompt

```text
- NEVER write unit tests after you write code. 
- Highly prefer E2E tests as the sole testing mechanism. Use them to verify complex features work. At the end of E2E tests, produce a verifiable and repeatable artifact. 
- If you must test a system in isolation, FIRST write all the ways it could fail, THEN write the code.
```

edits: removed the author's intro line ('At the top of my AGENTS.md:') and the quoted post link.
