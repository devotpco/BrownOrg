# Policy Binder

**0.1** This file is the policy binder of the project BrownOrg. The binder is the numbered record of the policies and decisions in force on the project. A policy that is not in the binder is not in force. The project manager keeps the binder. The Library note `Method/Cross_Functional_Team.md` defines the binder and the project manager's role. The Library is the folder `/Users/jerry/DEV/DEVLibrary/`, which holds rules and formats that any project may reuse.

**0.2** The Steward is the human who holds the decision on the project. AI stands for artificial intelligence. An AI on the project is any AI program that does work on the project. The orchestrator is the AI in conversation with the Steward. An agent is an AI that the orchestrator starts for one named task. `Method/Cross_Functional_Team.md` defines the Steward, the orchestrator and the agents.

**0.3** Each entry carries its own number: P-1, P-2, and so on. A number is never reused. An entry is never deleted. An entry that is no longer in force is marked retired, with the date.

**0.4** Each entry has four fields. **Date** is the date the policy was set. **Policy** states the policy in plain sentences and names every actor. **Origin** says who set the policy and when. Where the Steward set it, the Steward's words follow as a quotation. **Applies to** says where the policy applies. The Library note `Style/Outline_Numbering.md` §4.2 and §5.2 say how another passage cites an entry or a field.

**0.5** Paths in this file are given from the project's top folder.

## P-1 — The go rule

**Date.** 2026-09-28.

**Policy.** Outside the folder `0-AImemory/`, no AI on the project takes any action without an explicit go from the Steward. A go is the Steward's explicit word to go ahead with a step. An action is any tool call. A tool call is any step in which an AI does something beyond writing its reply in the conversation. Examples are a file edit, a shell command (a command run on the computer), a search, a memory write (a note saved to an AI's own memory) and an agent launch (the start of another AI). A question from the Steward gets a text-only answer: the AI answers in words and makes no tool call. An AI does not search for what the Steward or that AI likely already knows. The orchestrator reviews every question before it goes to the Steward, whether the orchestrator or an agent raised it. The orchestrator answers the question where it can and states the answer, so the Steward can veto it. Only a question that stays unresolved goes to the Steward. A request from the Steward that begins "Can you…" or "help me…" asks the AI for a proposal and gives no go. A direct instruction from the Steward, such as "read these files" or "rename it", is its own go. The AI states what it will do, then waits for the Steward's go. A go covers one step only. P-2 states the one exception to this rule.

**Origin.** The Steward's standing instructions to the AI, which hold in every session, as they read on 2026-09-28. The source, word for word:

> Claude takes no action without an explicit "go" from the user. Action means any tool call: a file edit, a shell command, a search, a memory write, an agent launch. A question gets a text-only answer. Don't search for what the user or Claude likely already knows. Claude reviews every question first, its own or an agent's, and answers it where it can, stating the answer so the user can veto it. Only what stays unresolved goes to the user. "Can you…" and "help me…" ask for a proposal, not permission. A direct instruction ("read these files", "rename it") is its own go. Claude states what it will do, then waits. When a "go" is given, it covers that one step only.

**Applies to.** Every tool call by any AI on the project, anywhere outside the folder `0-AImemory/`.

## P-2 — Autonomy inside 0-AImemory/

**Date.** 2026-09-28.

**Policy.** Inside the folder `0-AImemory/`, the AIs on the project have full autonomy. They create, read, update and delete files there without a go and without asking the Steward. The Steward does not read the folder and controls nothing in it. The folder is the AIs' memory for items related to this project. P-2 is the one exception to P-1.

**Origin.** The Steward, in conversation, 2026-09-28:

> I invoke the rule that 0-AImemory folder is the AIs' with full autonomy. I don't read it, or control anything in it. It is your memory for project-related memory.

**Applies to.** The folder `0-AImemory/` and every file in it, for every AI on the project.

## P-3 — Outline-numbering choices

**Date.** 2026-09-28.

**Policy.** The Library note `Style/Outline_Numbering.md` says how the project numbers the text of its documents. Its §1.2 requires each project to record three choices in one binder entry. Its §0.2 to §0.5 define the terms used below. The project's three choices are these:
- Documents exempt from outline numbering: none.
- Home documents:
  - `Objective.md`: what the project builds, why, and what success is.
  - `0-AImemory/BINDER.md`: policies and decisions.
  - `0-AImemory/RULES.md`: where things are, how this project applies the team rules, and who owns which file.
  - `9-Backlog/Parking_Lot/Parking_Lot.md`: items not being worked now, and open questions for the Steward.
  - `0-AImemory/HANDOFF.md`: the project's state, its change log, and its next steps.
- Items that already carry their own numbers, and so get no outline number: the entries in this binder (P-1, P-2, and so on), the questions in the parking lot (question 1, question 2, and so on), and the log entries in the change log of `0-AImemory/HANDOFF.md`.

**Origin.** The orchestrator set the three choices on 2026-09-28, as `Style/Outline_Numbering.md` §1.2 requires.

**Applies to.** Every project document, as `Style/Outline_Numbering.md` §0.2 defines the term.

## P-4 — The remote repository

**Date.** 2026-09-28.

**Policy.** The project keeps the history of its files in Git, a version-control program. Git records each saved set of changes as a commit. A remote repository is a copy of that history kept on another computer. To push is to send commits to the remote repository. The project's remote repository will be on GitHub, a service that hosts Git repositories. As of 2026-09-28, no remote repository exists and nothing has been pushed. No AI on the project creates the remote repository or pushes to it without the Steward's go, because each is an action under P-1.

**Origin.** The Steward, in conversation, 2026-09-28. The Steward wrote GH for GitHub:

> Project will go to GH, not yet?

**Applies to.** The project's Git history and any remote copy of it.
