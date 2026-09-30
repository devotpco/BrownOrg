# BrownOrg Resume File

**0.1** This is the resume file of the project named BrownOrg. An AI with no conversation behind it reads this file to continue the work.

**0.2** Read `0-AImemory/RULES.md` first. It says where things are, who owns which file, and where the team's terms are defined. Paths in this file are written as its §1.1 and §1.2 state.

**0.3** Tess, the tech writer, owns this file.

**0.4** §1, §3 and §4 are rewritten at every update, and their headings say so. `Style/Outline_Numbering.md` §4.3 states how the blocks in such a section are numbered and cited.

**0.5** §2 is the change log. Every entry stays, and a new entry is added at the end. Each entry keeps its own number and has no outline number (P-3). An entry is cited by file, kind and number, for example `HANDOFF.md` log entry 2.

**0.6** §5 and §6 are the two bookend checklists. They are not rewritten at every update.

## 1. State (rewritten at every update)

**1.1** This update was written on 2026-09-29.

**1.2** `Objective.md` is written. The Steward approved the v0 design on 2026-09-29. It is six drafts (`v0_UX.md`, `v0_Business.md`, `v0_Boundary.md`, `v0_Data_Model.md`, `v0_Data_Access.md`, `v0_Deployment.md`) and `v0_Requirements.md` (R-1 to R-9, plus two build checks). All seven are locked in `1-Design/Locked/`. Only the Steward approves an edit to them.

**1.3** The folder tree set out in `Method/Folder_Structure.md` exists in full. `0-AImemory/RULES.md` §3 maps it.

**1.4** No application code exists yet. `2-APP/main.py` is PyCharm's sample; it becomes the Worker's entry file. Tools on the Steward's machine: `uv` is installed. Homebrew could not install Node.js on the Steward's Intel Mac, so Node.js v24.21.0 and npm 11.19.0 are installed inside the venv `~/DEV_ENV/BrownOrg` through `nodeenv`. They are available when that venv is active. Cloudflare: the Steward's personal account; `wrangler login` has not yet been run.

**1.5** Git records the project. The repository was initialized on 2026-09-28. The first commit, on branch `master`, holds `README.md` and `.gitignore`. The second commit, on branch `dev_claude`, holds the rest of the files written on 2026-09-28. Work continues on `dev_claude`. `master` holds only those two files.

**1.6** The repository has a remote on GitHub: git@github.com:devotpco/BrownOrg.git, named `origin`. Both `master` and `dev_claude` are pushed to it and track it (P-4).

**1.7** There is no test runner yet.

**1.8** The policy binder holds eight entries: P-1, the go rule; P-2, on the AIs' autonomy inside `0-AImemory/`; P-3, this project's outline-numbering choices; P-4, on the remote repository; and P-5 to P-8, which hold the v0 decisions.

## 2. Change log

**2.1** Entries run oldest first.

**Log entry 1.** 2026-09-27. Another AI, Grok, built the folder tree. Grok also wrote the project's documents itself, without dispatching each document's owner to write it.

**Log entry 2.** 2026-09-28. The Steward ruled that Grok's documents be reverted. Reed, the janitor, deleted them. The owners then wrote them anew from the Library's notes. Tess wrote the eight READMEs, `0-AImemory/RULES.md` and this file. Paula wrote `Objective.md`, `0-AImemory/BINDER.md` and `9-Backlog/Parking_Lot/Parking_Lot.md`. The folder tree was kept. Reed also moved `main.py` from `2-APP/` back to the project root, copied `.gitignore` from the Library, and added the nine `.gitkeep` files. The COB initialized git.

**Log entry 3.** 2026-09-28. The Steward answered two questions the COB had raised. The first asked when the Steward will state the project's objective; `Objective.md` records the answer. The second concerned the project's remote repository; the answer is P-4. Paula wrote the parking lot with no open question.

**Log entry 4.** 2026-09-28. The Steward ruled that branch `master` holds only a short README at the project root and `.gitignore`, and that all other work is on branch `dev_claude` (`0-AImemory/RULES.md` §5.8). Tess wrote the root `README.md`.

**Log entry 5.** 2026-09-28. The Steward gave the GitHub repository address: git@github.com:devotpco/BrownOrg.git, named `origin`. The COB added the remote, and pushed `master` and `dev_claude` to it.

**Log entry 6.** 2026-09-28. Library changes, pushed to DEVLibrary: `Reference/CI_CD.md`; the curl exception in `Method/Cross_Functional_Team.md`; `Method/Agent_Optimization.md` (the agent-setup trial, with §5.7 on effort inheritance); `Reference/Layer_Encapsulation.md` (the Steward's layer rules, with §4.9); and a roster change: Bruno backend, Lena business logic, Finn frontend, Uma UX, Deacon deployment, Cyrus cloud; Marta and Ingrid widened; Vera retired.

**Log entry 7.** 2026-09-28. Effort definition files `.claude/agents/effort-{low,medium,high,xhigh}.md` were added. `/2-APP/config/` was gitignored. `Objective.md` was rewritten from the Steward's what and why. The evening bookend did not run that day.

**Log entry 8.** 2026-09-29. The v0 design was drafted, cut to the keep-it-simple scope (P-5) and approved. Requirements were written, merged to 9 and approved. `main.py` moved to `2-APP/main.py` as the Worker entry file, by the Steward's ruling. V1 backlog items were added (`Use_Case_Descriptions.md`, `Preferred_Stack_After_v0.md`, `Config_Step.md`). The dispatch log was started. The design bookend was held. The design was locked (seven files moved to `1-Design/Locked/`).

## 3. Decisions pending (rewritten at every update)

**3.1** None.

## 4. Next steps (rewritten at every update)

**4.1** The steps run in this order:

- **4.2** The Steward runs `npx wrangler login` with the venv active. It opens a browser sign-in.
- **4.3** The build starts with the two build checks in `v0_Requirements.md`.
- **4.4** Build to the design, with tests for R-1 to R-7.
- **4.5** Deploy by hand from `dev_claude`, on the Steward's go.
- **4.6** The Steward walks through R-8 and R-9 by hand.

## 5. Morning bookend

**5.1** The COB runs this checklist at the start of each working day, before any work. It adapts the morning bookend in `Method/Cross_Functional_Team.md`, under "The two bookends", to this project: there is no test runner yet. P-1 and P-2 govern each step.

- **5.2** Confirm that the branch checked out is the branch for continuing work that §1 names.
- **5.3** Fetch from `origin` and confirm that `dev_claude` is in sync with `origin/dev_claude`.
- **5.4** Run the test runner. There is no test runner yet: note that, and go on.
- **5.5** Read into the session the files that `0-AImemory/RULES.md` §2 lists. They include this file and the policy binder.
- **5.6** List the decisions pending in §3.
- **5.7** Report what changed on disk since the last wrap-up commit (§6.7), or, if there is no wrap-up commit yet, since the latest commit on `dev_claude`. `git status` shows the changes not yet committed. `git log` shows the commits made since.

## 6. Evening bookend

**6.1** The team runs this checklist at the end of each working day. It adapts the evening bookend in `Method/Cross_Functional_Team.md`, under "The two bookends", to the same facts as §5.1. P-1 and P-2 govern each step.

- **6.2** Hollis, the housekeeper, runs the test runner. There is no test runner yet: note that, and go on.
- **6.3** The COB lists every item that exists only in the conversation, and names an owner for each. No agent inherits the conversation; every agent is fresh.
- **6.4** Each owner integrates its items into its own files. Each owner is a fresh agent, briefed from the COB's list.
- **6.5** Tess rewrites this file: §1, §3 and §4 afresh, and a new entry at the end of §2.
- **6.6** Hollis verifies that every pointer resolves. A pointer is a reference from one file to another file or to a numbered block. It resolves when its target exists.
- **6.7** The COB commits on the branch for continuing work that §1 names, with the message "wrap-up" and the date. This is the wrap-up commit. The COB then pushes `dev_claude` to `origin`; the evening bookend carries the Steward's permission for this push (P-4).

**6.8** Once a test runner exists, the rule that ties each commit to its result applies. It is in `Method/Cross_Functional_Team.md`, under "Files the team keeps".

**6.9** The COB also makes the sweep of §6.3 at the end of each stage of work, and before any restart of its session. The Steward ruled this on 2026-09-29.
