# BrownOrg Resume File

**0.1** This is the resume file of the project named BrownOrg. An AI with no conversation behind it reads this file to continue the work.

**0.2** Read `0-AImemory/RULES.md` first. It says where things are, who owns which file, and where the team's terms are defined. Paths in this file are written as its §1.1 and §1.2 state.

**0.3** Tess, the tech writer, owns this file.

**0.4** §1, §3 and §4 are rewritten at every update, and their headings say so. `Style/Outline_Numbering.md` §4.3 states how the blocks in such a section are numbered and cited.

**0.5** §2 is the change log. Every entry stays, and a new entry is added at the end. Each entry keeps its own number and has no outline number (P-3). An entry is cited by file, kind and number, for example `HANDOFF.md` log entry 2.

**0.6** §5 and §6 are the two bookend checklists. They are not rewritten at every update.

## 1. State (rewritten at every update)

**1.1** This update was written on 2026-09-28.

**1.2** The Steward has not yet stated what the project builds, or why. `Objective.md` records when the Steward will state it.

**1.3** The folder tree set out in `Method/Folder_Structure.md` exists in full. `0-AImemory/RULES.md` §3 maps it.

**1.4** No design, no application code and no backlog item exists yet.

**1.5** Git records the project. The repository was initialized on 2026-09-28. The first commit, on branch `master`, holds `README.md` and `.gitignore`. The second commit, on branch `dev_claude`, holds the rest of the files written on 2026-09-28. Work continues on `dev_claude`. `master` holds only those two files.

**1.6** The repository has no remote yet (P-4).

**1.7** There is no test runner yet.

**1.8** The policy binder holds four entries: P-1, the go rule; P-2, on the AIs' autonomy inside `0-AImemory/`; P-3, this project's outline-numbering choices; and P-4, on the remote repository.

## 2. Change log

**2.1** Entries run oldest first.

**Log entry 1.** 2026-09-27. Another AI, Grok, built the folder tree. Grok also wrote the project's documents itself, without dispatching each document's owner to write it.

**Log entry 2.** 2026-09-28. The Steward ruled that Grok's documents be reverted. Reed, the janitor, deleted them. The owners then wrote them anew from the Library's notes. Tess wrote the eight READMEs, `0-AImemory/RULES.md` and this file. Paula wrote `Objective.md`, `0-AImemory/BINDER.md` and `9-Backlog/Parking_Lot/Parking_Lot.md`. The folder tree was kept. Reed also moved `main.py` from `2-APP/` back to the project root, copied `.gitignore` from the Library, and added the nine `.gitkeep` files. The orchestrator initialized git.

**Log entry 3.** 2026-09-28. The Steward answered two questions the orchestrator had raised. The first asked when the Steward will state the project's objective; `Objective.md` records the answer. The second concerned the project's remote repository; the answer is P-4. Paula wrote the parking lot with no open question.

**Log entry 4.** 2026-09-28. The Steward ruled that branch `master` holds only a short README at the project root and `.gitignore`, and that all other work is on branch `dev_claude` (`0-AImemory/RULES.md` §5.8). Tess wrote the root `README.md`.

## 3. Decisions pending (rewritten at every update)

**3.1** None. The parking lot, `9-Backlog/Parking_Lot/Parking_Lot.md`, holds no open question for the Steward.

## 4. Next steps (rewritten at every update)

**4.1** The steps run in this order:

- **4.2** On the Steward's go, the orchestrator creates the project's remote repository on GitHub, a web service that hosts git repositories, and pushes to it. Before it does, the orchestrator asks the Steward three things: the repository's name, the GitHub account it goes under, and whether it is private. P-4 governs this step.
- **4.3** The Steward states the project's objective: what it builds, and why.
- **4.4** Paula writes that objective into `Objective.md`.

**4.5** When the remote exists, Tess revises §5 and §6 so that the bookends fetch from it and push to it.

## 5. Morning bookend

**5.1** The orchestrator runs this checklist at the start of each working day, before any work. It adapts the morning bookend in `Method/Cross_Functional_Team.md`, under "The two bookends", to this project: there is no remote yet, and no test runner yet. P-1 and P-2 govern each step.

- **5.2** Confirm that the branch checked out is the branch for continuing work that §1 names.
- **5.3** Fetch from the remote and confirm the branch is in sync with it. There is no remote yet (P-4): note that, and go on.
- **5.4** Run the test runner. There is no test runner yet: note that, and go on.
- **5.5** Read into the session the files that `0-AImemory/RULES.md` §2 lists. They include this file and the policy binder.
- **5.6** List the decisions pending in §3.
- **5.7** Report what changed on disk since the last wrap-up commit (§6.7), or, if there is no wrap-up commit yet, since the latest commit on `dev_claude`. `git status` shows the changes not yet committed. `git log` shows the commits made since.

## 6. Evening bookend

**6.1** The team runs this checklist at the end of each working day. It adapts the evening bookend in `Method/Cross_Functional_Team.md`, under "The two bookends", to the same facts as §5.1. P-1 and P-2 govern each step.

- **6.2** Hollis, the housekeeper, runs the test runner. There is no test runner yet: note that, and go on.
- **6.3** Hollis lists every item that exists only in the conversation, and names an owner for each. For this one step Hollis inherits the conversation, under the exception that `Method/Cross_Functional_Team.md` states under "Terms".
- **6.4** Each owner integrates its items into its own files. Each owner is a fresh agent, briefed from Hollis's report.
- **6.5** Tess rewrites this file: §1, §3 and §4 afresh, and a new entry at the end of §2.
- **6.6** Hollis verifies that every pointer resolves. A pointer is a reference from one file to another file or to a numbered block. It resolves when its target exists.
- **6.7** The orchestrator commits on the branch for continuing work that §1 names, with the message "wrap-up" and the date. This is the wrap-up commit. Then the orchestrator pushes. There is no remote yet (P-4): note that the day's work is committed locally only.

**6.8** Once a test runner exists, the rule that ties each commit to its result applies. It is in `Method/Cross_Functional_Team.md`, under "Files the team keeps".
