# 9-Backlog

**0.1** This folder holds the features and functions that are not in the current version, and the project's parking lot.

**0.2** The Library is the shared set of notes on rules and formats that the project points at. Its `Method/Folder_Structure.md` sets out this folder's place in the project's layout. `0-AImemory/RULES.md` says where the Library is.

**0.3** The Steward is the human who decides for the project. The Library's `Method/Cross_Functional_Team.md` defines the role.

## 1. Sub-folders

**1.1** The features and functions are grouped by the version they are planned for, one sub-folder per version: `V1/`, `V2/`, and so on. The items for the next version go in `V1/`.

**1.2** An item in a version sub-folder is out of scope for the current version. It is not rejected.

**1.3** Each such item is one file, named for the feature, with a pointer to where its text last lived.

**1.4** `Parking_Lot/` holds one file, `Parking_Lot.md`. It lists items that belong to the project but are not being worked now. Examples are changes waiting on a locked design file (see `1-Design/README.md`), open questions for the Steward, and components stated but not designed.

**1.5** Each item in `Parking_Lot.md` names what it is, why it waits, and what unblocks it.

**1.6** `Method/Folder_Structure.md`, under the entry for `9-Backlog`, states when an item leaves the parking lot.
