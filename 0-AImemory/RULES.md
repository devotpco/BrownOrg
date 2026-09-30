# BrownOrg Rules File

**0.1** This is the rules file of the project named BrownOrg. It says where things are, how the team works on this project, and who owns which file. §2 says who reads it, and when.

**0.2** This file states how this project applies the rules its team holds. It does not restate those rules. It cites them where they are stated: in the Library (§1.2) and in the project's policy binder (§1.9).

**0.3** Tess, the team's tech writer, owns this file (§4).

## 1. Places and terms

**1.1** The project root is the folder `/Users/jerry/DEV/PyCharm/BrownOrg`. A path in this file that does not begin with `/`, `Method/` or `Style/` is relative to the project root.

**1.2** The Library is the folder `/Users/jerry/DEV/DEVLibrary/`. It holds notes on rules and formats that any project may use. A path in this file that begins with `Method/` or `Style/` is relative to the Library. `Method/Cross_Functional_Team.md`, under "Rules the team holds", states which way pointers between a project and the Library may run.

**1.3** This project follows four Library notes:

- **1.4** `Method/Cross_Functional_Team.md`: the team's roles, the files every project keeps, how work moves, and the two daily checks called bookends.
- **1.5** `Method/Folder_Structure.md`: the folder layout, and the rules for READMEs.
- **1.6** `Style/Man_from_Mars_Writing_Style.md`: the writing standard.
- **1.7** `Style/Outline_Numbering.md`: how each block of a project document is numbered and cited.

**1.8** `Method/Committee_Meeting_Format.md` describes an older team format. `Method/Cross_Functional_Team.md` replaced it, and this project does not use it.

**1.9** The policy binder is `0-AImemory/BINDER.md`. Its entries are numbered P-1, P-2, P-3 and onward. This file cites an entry by its number alone, as `Style/Outline_Numbering.md` §5.2 allows.

**1.10** `Method/Cross_Functional_Team.md` defines these terms under "Terms": the Steward, the COB (Chief of the Boat), an agent, a fresh agent, an owner, the rules file, the resume file, the policy binder, the backlog and the parking lot. In a few words: the Steward is the human, who holds every decision. An agent is an artificial-intelligence (AI) program given one named task. The COB is the AI in conversation with the Steward; it dispatches the agents. A fresh agent starts with only its directive. An owner is the one agent that may change a given file.

**1.11** `Style/Outline_Numbering.md` defines a block, a specification and a home document, in its §0.3 to §0.5.

**1.12** A go is the Steward's explicit permission for an action. P-1 states the rule that requires it.

**1.13** Git is the version-control program that records the project's files and their history. Its record is called the repository, and it sits in the project root. A commit is one recorded state of the files. A branch is a named line of commits. A remote is a copy of the repository kept on another computer. To push is to send commits to a remote. To fetch is to receive commits from one.

**1.14** PyCharm is the code editor used on this project. It keeps its settings in the folder `.idea/`.

## 2. Reading order at the start of a session

**2.1** At the start of every session, the COB reads these files, in this order:

- **2.2** `0-AImemory/RULES.md`, this file.
- **2.3** `0-AImemory/HANDOFF.md`, the resume file. It holds the project's state, its change log, the decisions pending, the next steps and the two bookend checklists.
- **2.4** `0-AImemory/BINDER.md`, the policy binder.
- **2.5** `Objective.md`, the objective statement.
- **2.6** `9-Backlog/Parking_Lot/Parking_Lot.md`, the parking lot.
- **2.7** `Method/Cross_Functional_Team.md` and `Method/Folder_Structure.md`, the two Method notes in §1.4 and §1.5.

**2.8** A fresh agent does not follow this list. It reads only what its directive names, as `Method/Cross_Functional_Team.md` states under "Terms".

**2.9** The two Style notes in §1.6 and §1.7 are read by an agent whose task writes or edits a document. That agent's directive names them. This narrower reading follows the no-ocean-boiling rule, which sizes work to the question, in `Method/Cross_Functional_Team.md` under "Rules the team holds".

## 3. Folder map

**3.1** The folder tree follows `Method/Folder_Structure.md`. Each folder's README says what the folder is for. The tree below shows every folder and every file the team keeps, `main.py` (§3.5) among them.

```
BrownOrg/
  .gitignore                also on branch master (§5.8)
  .claude/
    agents/
      effort-low.md
      effort-medium.md
      effort-high.md
      effort-xhigh.md
  Objective.md
  README.md                 also on branch master (§5.8)
  0-AImemory/
    README.md
    RULES.md
    HANDOFF.md
    BINDER.md
    Dispatch_Log.md
  1-Design/
    README.md
    Draft/
      .gitkeep
    Locked/
      .gitkeep
      v0_UX.md
      v0_Business.md
      v0_Boundary.md
      v0_Data_Model.md
      v0_Data_Access.md
      v0_Deployment.md
      v0_Requirements.md
  2-APP/
    README.md
    main.py                 the Worker's entry file (§3.5)
    Data/
      README.md
    Boundary/
      README.md
      Boundary_in/
        .gitkeep
      Boundary_out/
        .gitkeep
    Business/
      README.md
  8-History/
    README.md
    Revision/
      .gitkeep
    Archive/
      .gitkeep
    Errata/
      .gitkeep
  9-Backlog/
    README.md
    Parking_Lot/
      Parking_Lot.md
    V1/
      .gitkeep
      Use_Case_Descriptions.md
      Preferred_Stack_After_v0.md
      Config_Step.md
    V2/
      .gitkeep
```

**3.2** No folder for the kind of app, such as `html/` or `css/`, exists under `2-APP/` yet. The Steward has not yet stated what the project builds. `Objective.md` records the objective's status.

**3.3** Git does not record an empty folder. Each empty sub-folder therefore holds an empty file named `.gitkeep`, so that the folder exists in every copy of the repository. The tree in §3.1 shows all nine. A `.gitkeep` is not a README. The COB ruled on 2026-09-28 that a `.gitkeep` stays until its folder holds another file that git records. Tess may then remove it.

**3.4** `.gitignore`, at the root, lists the paths git does not record: `.idea/`, the folder where PyCharm keeps its settings; and `/2-APP/config/`, the folder that holds the app's configuration file, which may contain secrets. It was copied from the Library's own `.gitignore`.

**3.5** `2-APP/main.py`, in the app root, is the entry file of the Cloudflare Worker in v0. It only wires the endpoints together. Its PyCharm sample content is replaced during the build. Git records it. Bruno, the backend engineer, owns it, since it wires the boundary layer. The Steward ruled on 2026-09-29 that it belongs in the app root, not the project root. This replaces the ruling of 2026-09-28 that it had no owner.

**3.6** `.claude/agents/` holds four agent definition files: `effort-low.md`, `effort-medium.md`, `effort-high.md`, and `effort-xhigh.md`. Each file sets only reasoning effort and a `maxTurns` guard of 50. The COB chooses the model on each dispatch. Claude Code loads these definitions when a session starts. The Library note `Method/Agent_Optimization.md` states the approach.

## 4. Who owns which file

**4.1** `Method/Cross_Functional_Team.md` states the one-owner rule under "Rules the team holds". It lists the team's members and their roles under "The team", and this project uses those names. The table names the owner of each file the team keeps.

| File | What it is | Owner |
|---|---|---|
| `Objective.md` | The objective statement | Paula, project manager |
| `0-AImemory/BINDER.md` | The policy binder | Paula |
| `9-Backlog/Parking_Lot/Parking_Lot.md` | The parking lot | Paula |
| Each item file in `9-Backlog/V1/`, `9-Backlog/V2/` and any later version folder (none yet) | The backlog | Paula |
| `0-AImemory/RULES.md` | The rules file | Tess, tech writer |
| `0-AImemory/HANDOFF.md` | The resume file | Tess |
| `0-AImemory/Dispatch_Log.md` | The dispatch log: one line per agent dispatch, with setup, estimate, actual and outcome | Otto, agent optimizer |
| `README.md`, at the root | The repository's front page, also on branch `master` (§5.8) | Tess |
| `0-AImemory/README.md`, `1-Design/README.md`, `2-APP/README.md`, `2-APP/Data/README.md`, `2-APP/Boundary/README.md`, `2-APP/Business/README.md`, `8-History/README.md`, `9-Backlog/README.md` | The eight READMEs | Tess |
| `.gitignore` | The list of paths git does not record | Tess |
| `.claude/agents/effort-low.md`, `.claude/agents/effort-medium.md`, `.claude/agents/effort-high.md`, `.claude/agents/effort-xhigh.md` | Agent definition files that set reasoning effort | Otto, agent optimizer |
| The nine `.gitkeep` files shown in §3.1 | Markers that keep empty folders in git | Tess |
| `2-APP/main.py` | The Cloudflare Worker's entry file (§3.5) | Bruno, backend engineer |
| `1-Design/Locked/v0_UX.md` | The v0 UX design | Uma, UX designer |
| `1-Design/Locked/v0_Business.md` | The v0 business-logic design | Lena, business-logic engineer |
| `1-Design/Locked/v0_Boundary.md` | The v0 boundary design | Bruno |
| `1-Design/Locked/v0_Data_Model.md` | The v0 data model | Marta, data modeler |
| `1-Design/Locked/v0_Data_Access.md` | The v0 data-access design | Ingrid, schema architect |
| `1-Design/Locked/v0_Deployment.md` | The v0 deployment design | Deacon, deployment engineer |
| `1-Design/Locked/v0_Requirements.md` | The v0 requirements | Quill, QA |
| `9-Backlog/V1/Use_Case_Descriptions.md`, `9-Backlog/V1/Preferred_Stack_After_v0.md`, `9-Backlog/V1/Config_Step.md` | V1 backlog items | Paula |

**4.2** The COB ruled on 2026-09-28 that Tess owns `.gitignore` and the `.gitkeep` files, as part of the folder map.

**4.3** A file the team creates later gets a row in the table when it is created.

**4.4** `Method/Cross_Functional_Team.md`, under "Roles", states what the Steward and the COB may write.

**4.5** The full team roster and coverage areas follow. `Method/Cross_Functional_Team.md` under "The team" states each role.

| Member | Role | Owns in this project |
|---|---|---|
| Paula | Project manager | `Objective.md`, `0-AImemory/BINDER.md`, `9-Backlog/Parking_Lot/Parking_Lot.md`, and each backlog item file, among them `Use_Case_Descriptions.md`, `Preferred_Stack_After_v0.md` and `Config_Step.md` in `9-Backlog/V1/` |
| Tess | Tech writer | `0-AImemory/RULES.md`, `0-AImemory/HANDOFF.md`, every README, `.gitignore`, and the `.gitkeep` files (§4.1) |
| Quill | QA | `1-Design/Locked/v0_Requirements.md` |
| Ingrid | Schema architect | `1-Design/Locked/v0_Data_Access.md` |
| Hal | Vocabulary designer | No file yet |
| Marta | Data modeler | `1-Design/Locked/v0_Data_Model.md` |
| Bruno | Backend engineer | `2-APP/main.py` (§3.5) and `1-Design/Locked/v0_Boundary.md` |
| Lena | Business-logic engineer | `1-Design/Locked/v0_Business.md` |
| Finn | Frontend developer | No file yet |
| Uma | UX designer | `1-Design/Locked/v0_UX.md` |
| Deacon | Deployment engineer | `1-Design/Locked/v0_Deployment.md` |
| Cyrus | Cloud engineer | No file yet |
| Reed | Janitor | Owns nothing |
| Mara | Archivist | No file yet |
| Rhea | Analyst | No file yet |
| Ada | Auditor | Owns nothing |
| Sam | Scout | Owns nothing |
| Nell | Cold reader | Owns nothing |
| Hollis | Housekeeper | Owns nothing |
| Otto | Agent optimizer | `0-AImemory/Dispatch_Log.md`, and the four agent definition files in `.claude/agents/`: `effort-low.md`, `effort-medium.md`, `effort-high.md` and `effort-xhigh.md` (§3.6). The Steward ruled on 2026-09-29 that Otto owns them, taking them over from Tess. Otto runs at least daily or on the COB's request, and records each set of dispatches. |

## 5. How the team works on this project

**5.1** The team works in the format that `Method/Cross_Functional_Team.md` states.

**5.2** P-1, the go rule, governs every action outside `0-AImemory/`.

**5.3** P-2 governs every action inside `0-AImemory/`. The COB ruled on 2026-09-28 that P-2 gives the AIs autonomy toward the Steward only: no go and no questions. Among the AIs, the rules in `Method/Cross_Functional_Team.md`, one owner per file among them, still hold inside `0-AImemory/`.

**5.4** The COB runs the project's git commands and makes its commits, as its role under "The COB" in `Method/Cross_Functional_Team.md` states.

**5.5** P-4 governs the project's remote repository.

**5.8** The Steward ruled on 2026-09-28 that the project's branches follow the standard practice of continuous integration and continuous delivery (CI/CD). Work is done on branch `dev_claude`. Work reaches branch `master` only by promotion: it moves forward from one branch to the next, through intermediate branches such as a quality assurance (QA) branch and a staging branch, where work gets a last check before `master`. Those intermediate branches are not set up yet, and their names are not fixed. No one commits to `master` directly. Until the first promotion, `master` holds only the root `README.md` and `.gitignore`.

**5.6** The two bookends are the checks the team runs at the start and at the end of each working day. They run from the checklists in `0-AImemory/HANDOFF.md` §5 and §6.

**5.7** The test runner is the program that runs the project's tests. The rule that ties each commit to its result is in `Method/Cross_Functional_Team.md`, under "Files the team keeps". `0-AImemory/HANDOFF.md` §1 records whether a test runner exists yet.

## 6. Where project substance may live

**6.1** Project substance is content specific to this project. `Method/Cross_Functional_Team.md`, under "Rules the team holds", states where it may be written. `Method/Folder_Structure.md`, under the entry for `0-AImemory`, states the folder that serves that rule.

**6.2** In this project, the project's own tree is the project root (§1.1) and everything under it.

**6.3** An AI's working notes about this project go in `0-AImemory/`. `0-AImemory/README.md` says what that folder holds and what it does not.

## 7. Writing standard

**7.1** The writing standard for every lasting document is `Style/Man_from_Mars_Writing_Style.md`, as `Method/Cross_Functional_Team.md` states under "What was kept from the committee format". Its major standard is the stranger test. Its minor standard is Katra voice, its rules for sentences.

**7.2** Every project document is numbered and cited as `Style/Outline_Numbering.md` states. P-3 records this project's choices under that note's §1.2.

**7.3** `Style/Outline_Numbering.md` §7 states that each specification has one home document. P-3 names this project's home documents.
