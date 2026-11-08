# agents-stuff

agent skills and prompts collected from x, one file per entry.

## Skills

### automation

| name | author | description |
| --- | --- | --- |
| [better-github-skill](skills/automation/better-github-skill.md) | [@avgvstvs96](https://x.com/avgvstvs96) | A skill with scripts (pr-snapshot, pr-threads, pr-watch, ci-failures) so agents use gh in one bounded call instead of long loops, built from analysis of 1,800+ real agent gh calls. |
| [lever](skills/automation/lever.md) | [@_Evan_Boyle](https://x.com/_Evan_Boyle) | GitHub's Copilot plugin of skills and automations for building feedback loops for coding agents, mined from engineers' pooled session history. Shared by @_Evan_Boyle. |

### coding

| name | author | description |
| --- | --- | --- |
| [antithesis-skills](skills/coding/antithesis-skills.md) | [@GeoffreyHuntley](https://x.com/GeoffreyHuntley) | Antithesis's skill pack for researching, setting up, launching and triaging Antithesis tests to catch correctness faults. @GeoffreyHuntley says it's useful even without the full Antithesis platform. |
| [code-like-luke](skills/coding/code-like-luke.md) | [@LukeParkerDev](https://x.com/LukeParkerDev) | @LukeParkerDev's /code-like-luke OpenCode slash command for happy-path-first, use-case-oriented design with clear orchestration and strong interfaces. He calls it a 'free deslop alpha'. |
| [coding-standards.md and errors.md](skills/coding/coding-standards-and-errors.md) | [@dillon_mulroy](https://x.com/dillon_mulroy) | Two portable agent docs @dillon_mulroy carries from project to project instead of many skills: coding standards (monorepo boundaries and more) and error design principles for messages that help humans and agents. |
| [ub-mode](skills/coding/ub-mode.md) | [@unclebobmartin](https://x.com/unclebobmartin) | Uncle Bob's coding skill that enforces 'first make it work, then make it right, then follow practice', loosely based on poteto's pstack rules and paired with his crapper, dryer and mutator quality-gate tools. |

### design

| name | author | description |
| --- | --- | --- |
| [diorama ui skills](skills/design/diorama-ui-skills.md) | [@domgor](https://x.com/domgor) | Claude skills (design-component, diorama-ui-craft, review-ui and more) from the open-source Diorama design system, featured in a Codrops guide by Jakub Otcenas on building with Paper and Claude Code agents that know your taste. @domgor shared the writeup. |
| [interface-bts](skills/design/interface-bts.md) | [@Nomandsign](https://x.com/Nomandsign) | A skill that draws a spec poster of an interaction in a React project, pausing the real component at key moments and annotating dimensions, easing curves and timings. @Nomandsign's post links an essay on designing it like an app with two users, the human and the agent. |
| [joe-bell/skills (apple-web-app)](skills/design/joe-bell-skills.md) | [@joebell_](https://x.com/joebell_) | @joebell_'s public skills repo, led by apple-web-app for building web apps that feel native in iOS, iPadOS and macOS Safari, plus letterboxd-diary and elron. |
| [lieflat-charts](skills/design/lieflat-charts.md) | [@lieflat_3](https://x.com/lieflat_3) | An open-source data-visualization and report skill that makes polished, interactive HTML charts (60+ chart types, mono plus three color themes) for Claude Code, Codex and other agents. Post by @lieflat_3 is in Chinese. |
| [prefer-container-queries](skills/design/prefer-container-queries.md) | [@flornkm](https://x.com/flornkm) | Steers agents to Tailwind container queries over viewport breakpoints so components adapt to their container's width wherever they're placed. @flornkm's first published skill. |

### meta

| name | author | description |
| --- | --- | --- |
| [be-ambitious](skills/meta/be-ambitious.md) | [@daniel_mac8](https://x.com/daniel_mac8) | /be-ambitious rewrites a task into a deeper version of itself, not a bigger one, by naming what a top professional would do, their raw sources, methods and what would prove the result right. Adapted by @daniel_mac8 from Felix Rieseberg's prompt. |
| [pstack](skills/meta/pstack.md) | [@poteto](https://x.com/poteto) | @poteto's skill pack for high-quality agent coding (poteto-mode, /correct, /architect, /recall, /sharpen, /benchmark-checklist and more). The 0.15.9 release post adds /correct, which turns repeated corrections into architecture, types and checks; @DmitriyLeybel also posted an Opus-written deep dive on it. The state-machine follow-up pairs /create-formal-verification-skill, which generates project-local checks for a scoped property, with /statechart, which checks TLA+ models and visualizes user flows as Mermaid statecharts with shortest paths to rule violations. |

### research

| name | author | description |
| --- | --- | --- |
| [web-search](skills/research/web-search.md) | [@cancelik](https://x.com/cancelik) | A harness-agnostic skill that searches Google or DuckDuckGo through a local browser (CDP) and reads selected pages as Markdown, as a free alternative to paid search services. By @cancelik. |

### security

| name | author | description |
| --- | --- | --- |
| [security-audit](skills/security/security-audit.md) | [@CloudflareDev](https://x.com/CloudflareDev) | Cloudflare's open-source skill that turns a coding agent into a team of security auditors, running a six-phase audit from recon and coverage-led hunting to independently verified findings and reports. Posted by @CloudflareDev; it seeded Cloudflare's vulnerability discovery harness. |

### writing

| name | author | description |
| --- | --- | --- |
| [anti-slop writing skills (top 10)](skills/writing/anti-slop-skills-roundup.md) | [@juampitech](https://x.com/juampitech) | @juampitech's ranked list of ten anti-slop writing skills: stop-slop, no-ai-slop, humanizer (blader), unslop, slopbeth, humanizer (Aboudjem), deslop, anti-slop, humanize and anti-ai-slop-writing. Links in the order of the post. |
| [attention-kind output style](skills/writing/attention-kind.md) | [@daniel_mac8](https://x.com/daniel_mac8) | An ADHD-friendly Claude Code output style from @alexgreensh's attention-span repo: answer first, short, arrow-marked points with bold key words. @daniel_mac8 cites 43% shorter output with the same coding pass rate. |
| [simplified technical english skills](skills/writing/simplified-technical-english-skills.md) | [@andrew_n_carr](https://x.com/andrew_n_carr) | @andrew_n_carr's roundup of community skills built on ASD-STE100 Simplified Technical English to curb agents' invented jargon: a Claude skill, an STE skill kit, writing styles, a runbook skill and an STE checker. |
| [write-like-leopold](skills/writing/write-like-leopold.md) | [@reach_vb](https://x.com/reach_vb) | A Codex skill for drafting high-stakes investor, partner and incident communications in a direct, candid register inspired by Leopold Aschenbrenner's LP letter. Shared by @reach_vb as a gist. |

## Prompts

### coding

| name | author | description |
| --- | --- | --- |
| [dara's agents.md (excerpt)](prompts/coding/dara-agents-md.md) | [@daradoescode](https://x.com/daradoescode) | An excerpt of @daradoescode's AGENTS.md for the Weaver widget framework: named concepts (landmine, receipt, tripwire, simple, obvious) and build philosophies. Her linked X article walks through how she wrote it. |
| [e2e-first testing rules](prompts/coding/e2e-first-testing-rules.md) | [@anshnanda](https://x.com/anshnanda) | AGENTS.md testing rules from @anshnanda: no post-hoc unit tests, prefer E2E tests that produce a verifiable artifact, and list failure modes before writing isolated code. |
| [fix sequential async calls](prompts/coding/fix-sequential-async-calls.md) | [@_dylanga](https://x.com/_dylanga) | A one-line prompt from @_dylanga that scans hot paths for needless sequential async calls; he says the diffs are easy to review. |
| [justify yourself](prompts/coding/justify-yourself.md) | [@elithrar](https://x.com/elithrar) | Two prompts from @elithrar that force the agent to justify its work: a call graph of changes vs main, and a stack-ranked review of every test with removal candidates. |
| [marcos hernanz's agents.md](prompts/coding/marcos-agents-md.md) | [@MarcosHernanz](https://x.com/MarcosHernanz) | @MarcosHernanz's full AGENTS.md after ~60B tokens: no backward compatibility, the simplest implementation, grow in layers, prefer established libraries, long-term architecture. He says he only uses it on side projects. |
| [precise naming](prompts/coding/precise-naming.md) | [@usgraphics](https://x.com/usgraphics) | A CLAUDE.md naming rule from @usgraphics: every name must use precise professional vocabulary, 'the word a 1972 IBM engineer would write in a specification'. |
| [web font optimization](prompts/coding/web-font-optimization.md) | [@shuding](https://x.com/shuding) | @shuding's full prompt for shrinking a site's web fonts (subsetting, axis trimming, core/extended split with unicode-range) while proving rendering stays pixel-identical. |

### design

| name | author | description |
| --- | --- | --- |
| [describe the ux](prompts/design/describe-the-ux.md) | [@steveruizok](https://x.com/steveruizok) | @steveruizok's ask to have an agent describe the UX of your application completely, which surfaces inconsistencies, bugs and design errors. He packaged it as a /product-description skill. |
| [ux, dx and ax agents.md lines](prompts/design/ux-dx-ax-agents-md-lines.md) | [@Voxyz_ai](https://x.com/Voxyz_ai) | Two AGENTS.md lines from @Voxyz_ai: cut taglines and helper text, and make decisions that improve user, developer and agent experience together. |

### meta

| name | author | description |
| --- | --- | --- |
| [agent-ergonomic system plan](prompts/meta/agent-ergonomic-system-plan.md) | [@doodlestein](https://x.com/doodlestein) | @doodlestein's follow-up prompt for after an agent drafts a project plan: rework the design so the system is agent-intuitive, agent-ergonomic and agent-accretive. |
| [expert prompt rewrite (spanish)](prompts/meta/expert-prompt-rewrite-es.md) | [@Adamaestr0_](https://x.com/Adamaestr0_) | A Spanish version of Felix Rieseberg's 'be more ambitious' suffix: add four lines asking what an expert would do, then have Claude rewrite your prompt. Posted by @Adamaestr0_. |
| [restate my goals](prompts/meta/restate-my-goals.md) | [@poteto](https://x.com/poteto) | @poteto's frequently used prompt asking the agent to restate your goals and the problem in its own words; it later became the in-your-own-words skill in pstack. |
| [trust your agents' work](prompts/meta/trust-your-agents-work.md) | [@poteto](https://x.com/poteto) | @poteto's paste-to-your-agent guide: invest most in codebase improvements, then static analysis, then prose, least in human review, followed by a pstack project prompt to make your code more agent friendly. |

### security

| name | author | description |
| --- | --- | --- |
| [chromium and electron cleanup](prompts/security/chromium-electron-cleanup.md) | [@dave_deguzza](https://x.com/dave_deguzza) | A Claude Code prompt from @dave_deguzza that deletes old Playwright/Puppeteer Chromium builds, sandboxes the Playwright MCP onto system Chrome, and audits Electron app versions. |

### writing

| name | author | description |
| --- | --- | --- |
| [remove mannered prose](prompts/writing/remove-mannered-prose.md) | [@omarsar0](https://x.com/omarsar0) | Anthropic's documented instruction against 'mannered prose' for Claude Fable 5.1, which @omarsar0 tested to cut 'claudese'. Source: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-fable-5-1#writing-density |
| [simplified technical english](prompts/writing/simplified-technical-english.md) | [@daniel_mac8](https://x.com/daniel_mac8) | @daniel_mac8's tip: tell Claude to write in ASD-STE100 Simplified Technical English and follow Zinsser's four principles of quality writing. |
| [writing-pr](prompts/writing/writing-pr.md) | [@LukeParkerDev](https://x.com/LukeParkerDev) | @LukeParkerDev's writing-pr skill for concise PR titles and bodies: mermaid diagrams, code samples and before/after tables instead of essays or 'I ran tests' notes. |
