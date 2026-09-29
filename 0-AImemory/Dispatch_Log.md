# Dispatch Log

Each line records one agent dispatch: its setup, the estimate, the actual and the outcome. The orchestrator uses it to learn which setups suit which tasks. The approach is in the Library note `/Users/jerry/DEV/DEVLibrary/Method/Agent_Optimization.md` (§12 describes this log).

"inherited" effort means the agent had no effort file and ran at the session's xhigh.

| # | date | owner | task | model | effort | estimate (time / tool calls) | actual (time / tool calls) | fix rounds | outcome |
|---|------|-------|------|-------|--------|------------------------------|----------------------------|------------|---------|
| 1 | 2026-09-28 | Reed | delete Grok files, move main.py, .gitkeep | Haiku | inherited | — | 1.1 min / 6 | 0 | ok |
| 2 | 2026-09-28 | Paula | Objective, binder, parking lot | Opus | inherited | — | 9.4 min / 8 | 2 | ok |
| 3 | 2026-09-28 | Tess | READMEs, rules file, resume file | Opus | inherited | — | 18.1 min / 16 | 4 | ok |
| 4 | 2026-09-28 | Mara | CI/CD Library note | Opus | inherited | 10 min / 12 | 4.5 min / 19 | 0 | ok, over tool estimate |
| 5 | 2026-09-28 | lookup agent | Claude Code docs lookup | Sonnet | inherited | 2 min / 8 | 1.7 min / 4 | 0 | ran curl unasked; curl rule created |
| 6 | 2026-09-28 | Mara | curl rule in Method | Sonnet | inherited | 3 min / 8 | 0.45 min / 2 | 0 | ok |
| 7 | 2026-09-28 | Rhea | research, Anthropic sources | Sonnet | inherited | 5 min / 12 | 1.4 min / 11 | 0 | ok |
| 8 | 2026-09-28 | Rhea | research, wider web | Sonnet | inherited | 5 min / 12 | 2.3 min / 13 | 0 | one over budget; dropped unverifiable numbers |
| 9 | 2026-09-28 | Tess | first agent definition files | Haiku | inherited | 1 min / 5 | 0.2 min / 4 | 0 | first attempt blocked (unapproved) |
| 10 | 2026-09-28 | Mara | Agent Optimization note | Sonnet | inherited | 4 min / 8 | 2.8 min / 6 | 1 | ok |
| 11 | 2026-09-28 | Tess | effort definition files | Haiku | inherited | 2 min / 12 | 1.6 min / 12 | 0 | ok, at budget |
| 12 | 2026-09-28 | Paula | binder P-4 | Haiku | low | 1 min / 4 | 0.5 min / 2 | 2 | brief was loose (orchestrator's fault) |
| 13 | 2026-09-28 | Tess | resume file, remote | Haiku | low | 2 min / 8 | 1.1 min / 7 | 1 | ok |
| 14 | 2026-09-28 | Rhea | Cloudflare languages | Sonnet | medium | 5 min / 14 | 1.9 min / 14 | 0 | ok, at budget |
| 15 | 2026-09-28 | Tess | .gitignore config folder | Haiku | low | 1 min / 5 | 0.3 min / 4 | 0 | ok |
| 16 | 2026-09-28 | Mara | Layer Encapsulation note | Sonnet | medium | 5 min / 10 | 2.0 min / 9 | 0 | ok |
| 17 | 2026-09-28 | Paula | Objective rewrite | Sonnet | medium | 3 min / 6 | 0.35 min / 3 | 0 | ok |
| 18 | 2026-09-28 | Mara | roster change, effort finding | Sonnet | medium | 4 min / 10 | 0.3 min / 7 | 0 | ok |
| 19 | 2026-09-28 | Tess | BrownOrg roster | Haiku | low | 1 min / 5 | 0.5 min / 2 | redo | fell short: partial roster |
| 20 | 2026-09-28 | Tess | BrownOrg roster (redo of 19) | Sonnet | low | — / 4 | 0.3 min / 3 | 0 | ok |
| 21 | 2026-09-28 | Mara | rule 5 clarification | Sonnet | low | 1 min / 3 | 0.2 min / 3 | 0 | ok |
| 22 | 2026-09-29 | Rhea | Cloudflare follow-up | Sonnet | medium | 4 min / 10 | 0.9 min / 9 | 0 | two questions unanswered |
| 23 | 2026-09-29 | Uma | v0 UX draft | Sonnet | medium | 3 min / 6 | 0.8 min / 4 | 3 | ok |
| 24 | 2026-09-29 | Lena | v0 business draft | Sonnet | medium | 3 min / 6 | 0.7 min / 5 | 1 | ok |
| 25 | 2026-09-29 | Bruno | v0 boundary draft | Sonnet | medium | 3 min / 6 | 0.4 min / 4 | 3 | renumbered blocks against the rule; fixed |
| 26 | 2026-09-29 | Marta | v0 data model draft | Sonnet | medium | 3 min / 6 | 0.4 min / 3 | 1 | ok |
| 27 | 2026-09-29 | Ingrid | v0 data access draft | Sonnet | medium | 3 min / 6 | 0.4 min / 3 | 2 | placeholder table name (parallel run) |
| 28 | 2026-09-29 | Deacon | v0 deployment draft | Sonnet | medium | 3 min / 6 | 0.7 min / 5 | 4 | ok; stopped at budget twice |
| 29 | 2026-09-29 | Tess | readability pass, six drafts | Sonnet | low | 1.5 min / 8 | 0.4 min / 8 | 1 | budget too tight (orchestrator's estimate) |
| 30 | 2026-09-29 | Paula | design check against binder | Sonnet | low | 1.5 min / 8 | 0.1 min / 1 | 0 | ok |
| 31 | 2026-09-29 | Paula | V1 backlog item | Sonnet | low | — / 3 | 0.2 min / 2 | 0 | ok |
| 32 | 2026-09-29 | Reed | move main.py to 2-APP | Haiku | low | — / 1 | 0.15 min / 1 | 0 | ok |
| 33 | 2026-09-29 | Tess | main.py in .gitignore and rules | Sonnet | low | — / 4 | 0.7 min / 9 | 2 | budget too tight (orchestrator's estimate) |
| 34 | 2026-09-29 | Tess | start dispatch log | Sonnet | low | — / 5 | 0.4 min / 4 | 0 | ok |
| 35 | 2026-09-29 | Deacon | config folder in deployment draft | Sonnet | medium | — / 1 | 0.1 min / 1 | 0 | ok |
| 36 | 2026-09-29 | Quill | v0 requirements | Sonnet | medium | 2 min / 10 | 0.8 min / 9 | 2 | 23 requirements, later merged |
| 37 | 2026-09-29 | Quill | apply first-review answers | Sonnet | medium | — / 5 | 1.5 min / 6 | 0 | one over budget |
| 38 | 2026-09-29 | Quill | merge requirements to 9 | Sonnet | medium | — / 3 | 0.3 min / 1 | 0 | ok |
| 39 | 2026-09-29 | Hollis | design bookend sweep (fork) | Opus 5.5 | session (xhigh) | — | 2.1 min / 1; about 631,000 tokens | 0 | ok; a fork carries the whole conversation, so it is the costliest run |

## Lessons so far

**1. Effort level drives speed.** Inherited xhigh effort made Opus runs slow; with effort files, Sonnet at medium does drafts and research in under two minutes, and Sonnet at low does single edits in seconds.

**2. Haiku suits mechanical work only.** Haiku at low effort suits purely mechanical work and fell short on a small judgment (row 19; redo row 20).

**3. Tool budgets.** Allow one call per separate edit plus one or two reads; estimates for many-edit tasks were too tight (rows 29, 33).

**4. Old time estimates are stale.** Time estimates made before the effort files are now too high.

**5. Keep the first review on.** Agents sometimes add small unrequested details (row 25).

**7. Overruns and resumes.** Many-edit tasks still ran over their tool budgets (rows 29, 33, 37). Resuming an agent for a fix round costs 5 to 15 seconds.

**8. Forks are costly.** The bookend fork (row 39) cost about 631,000 tokens, far more than any fresh agent.

**6. Planned comparisons.** Haiku at medium against Sonnet at low on a small judgment task; Opus at low against Sonnet at medium on a cold read.
