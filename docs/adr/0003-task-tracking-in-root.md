# Task tracking centralised in the orchestrator repo

Daily work logs and forward planning live in the root repo (`docs/tasks/YYYY-MM-DD.md` and `TASKS.md`), not inside individual project submodules. Project repos contain only code.

`TASKS.md` serves as the forward-looking backlog and the bridge to any external ticket system. `docs/tasks/YYYY-MM-DD.md` records completed and in-progress work per day, with commit SHAs inline for traceability.

This keeps planning in one place, makes cross-project work surfaceable in meetings, and positions the root repo as the natural interface for future automation.
