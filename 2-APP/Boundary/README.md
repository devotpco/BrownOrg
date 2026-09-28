# Boundary

**0.1** This folder holds every external connection of the application (app), in or out.

**0.2** The Library is the shared set of notes on rules and formats that the project points at. Its `Method/Folder_Structure.md` sets out this folder's place in the project's layout. `0-AImemory/RULES.md` says where the Library is.

**0.3** An external connection is a call that crosses the app's edge, in either direction. `Method/Folder_Structure.md` defines the term under "Terms".

**0.4** The folder keeps external connections apart from the business logic and from every other internal part of the app. `Method/Folder_Structure.md` states the rule under the entry for `2-APP`.

## 1. Sub-folders

**1.1** `Boundary_out/` holds files and folders that make calls out of the app. An example is a request to another service's application programming interface (API), the set of requests that service accepts.

**1.2** When it is unclear whether a file belongs in `Boundary_out/`, `Method/Folder_Structure.md`, under the entry for `2-APP`, says how the question is settled.

**1.3** `Boundary_in/` holds files and folders that receive calls into the app. Examples are the APIs the app exposes, and webhooks: addresses the app exposes so that another service can call back to it.
