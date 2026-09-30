# Policy Binder

**0.1** This file is the policy binder of the project BrownOrg. The binder is the numbered record of the policies and decisions in force on the project. A policy that is not in the binder is not in force. The project manager keeps the binder. The Library note `Method/Cross_Functional_Team.md` defines the binder and the project manager's role. The Library is the folder `/Users/jerry/DEV/DEVLibrary/`, which holds rules and formats that any project may reuse.

**0.2** The Steward is the human who holds the decision on the project. AI stands for artificial intelligence. An AI on the project is any AI program that does work on the project. The COB is the AI in conversation with the Steward. An agent is an AI that the COB starts for one named task. `Method/Cross_Functional_Team.md` defines the Steward, the COB and the agents.

**0.3** Each entry carries its own number: P-1, P-2, and so on. A number is never reused. An entry is never deleted. An entry that is no longer in force is marked retired, with the date.

**0.4** Each entry has four fields. **Date** is the date the policy was set. **Policy** states the policy in plain sentences and names every actor. **Origin** says who set the policy and when. Where the Steward set it, the Steward's words follow as a quotation. **Applies to** says where the policy applies. The Library note `Style/Outline_Numbering.md` §4.2 and §5.2 say how another passage cites an entry or a field.

**0.5** Paths in this file are given from the project's top folder.

## P-1 — The go rule

**Date.** 2026-09-28.

**Policy.** Outside the folder `0-AImemory/`, no AI on the project takes any action without an explicit go from the Steward. A go is the Steward's explicit word to go ahead with a step. An action is any tool call. A tool call is any step in which an AI does something beyond writing its reply in the conversation. Examples are a file edit, a shell command (a command run on the computer), a search, a memory write (a note saved to an AI's own memory) and an agent launch (the start of another AI). A question from the Steward gets a text-only answer: the AI answers in words and makes no tool call. An AI does not search for what the Steward or that AI likely already knows. The COB reviews every question before it goes to the Steward, whether the COB or an agent raised it. The COB answers the question where it can and states the answer, so the Steward can veto it. Only a question that stays unresolved goes to the Steward. A request from the Steward that begins "Can you…" or "help me…" asks the AI for a proposal and gives no go. A direct instruction from the Steward, such as "read these files" or "rename it", is its own go. The AI states what it will do, then waits for the Steward's go. A go covers one step only. P-2 states the one exception to this rule.

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

**Origin.** The COB set the three choices on 2026-09-28, as `Style/Outline_Numbering.md` §1.2 requires.

**Applies to.** Every project document, as `Style/Outline_Numbering.md` §0.2 defines the term.

## P-4 — The remote repository

**Date.** 2026-09-28.

**Policy.** The project keeps the history of its files in Git, a version-control program. Git records each saved set of changes as a commit. A remote repository is a copy of that history kept on another computer. To push is to send commits to the remote repository. The project's remote repository is on GitHub, a service that hosts Git repositories. As of 2026-09-28, the remote repository exists at git@github.com:devotpco/BrownOrg.git, named `origin`. The COB added it and pushed the branches `master` and `dev_claude` to it on the Steward's go, on 2026-09-28. No AI on the project creates a remote repository or pushes to it without the Steward's go, because each is an action under P-1. The evening bookend carries the Steward's permission for its push; at the evening wrap-up, the COB pushes `dev_claude` to `origin` without a separate go. Every other push needs the Steward's go under P-1. The GitHub repository `devotpco/BrownOrg` is private.

**Origin.** The Steward, in conversation, 2026-09-28. The Steward wrote GH for GitHub:

> Project will go to GH, not yet?

The Steward, 2026-09-28, on whether the repository is public or private:

> private

The Steward, 2026-09-28:

> evening bookend does include a push permission

**Applies to.** The project's Git history and any remote copy of it.

## P-5 — v0 scope: keep it simple

**Date.** 2026-09-29.

**Policy.** Version 0 (v0) builds only two things: an expense intake form and one table that saves the entries. The team designs nothing for later versions in v0. Enterprise features, real accounting and bank sync are all left out of v0. No AI on the project bakes any of them into v0.

**Origin.** The Steward, 2026-09-29:

> on all your points, K.I.S.S: keep it simple, Don't fuss over getting all the fields right or doing the accounting right, etc. The only real feature we are building is a SIMPLE intake table for expenses and a table to save the entries in. After v0, everything will change to make it enterprise-grade, real accounting, bank sync, etc, etc. If your team tries to bake any of that in for v0, we will have a problem. That's boiling v0!

**Applies to.** Every v0 design and build task, for every AI on the project.

## P-6 — v0 security

**Date.** 2026-09-29.

**Policy.** The only security in v0 is the login page, which is the home page. The login page checks one shared password that is fixed in the code. v0 has no sessions, no signed-in checks and no sign-out. The endpoints are unprotected. The password's value appears in no document, and no AI on the project writes it into one.

**Origin.** The Steward, 2026-09-29:

> login: nowhere in v0. The only security is a single login page that is the home page. If I get past that, I am in and testing

The Steward, 2026-09-28:

> In the code is fine for now. We will add security, members, roles and permissions, OAuth later

**Applies to.** The v0 login page, the v0 endpoints, and every project document (none may state the password).

## P-7 — v0 environments and deployment

**Date.** 2026-09-29.

**Policy.** DEV is any developer machine; the Steward has two. PROD is Cloudflare. v0 has no QA server. v0 uses one Worker and one D1 database, both named `brownorg`. Access to Cloudflare is by `wrangler login`; v0 uses no API key. Deploys are by hand from the branch `dev_claude`, and only on the Steward's go under P-1.

**Origin.** The Steward, 2026-09-29:

> DROP Local from the YAML; DEV is the developer machine setup, any dev machine. I have 2. PROD is the CF host. For v0, no QA server

The Steward, 2026-09-28:

> For v0 we will deploy on dev_claude and test on dev_claude for the live site testing

**Applies to.** v0 environments, deploys and Cloudflare access.

## P-8 — Stack choices

**Date.** 2026-09-28.

**Policy.** The stack adapts to what Cloudflare allows. The front end is Vue with PrimeVue, so that the Steward can understand the user interface.

**Origin.** The Steward, 2026-09-28:

> We adapt our stack to what cloudflare allows.

> I have a preference for using Vue (eg PrimeVue) just because I am not a front-end engineer and, I want to be able to understand the UXI, if I ask about it. React goes over my head

**Applies to.** Every choice of language, framework or library on the project.
