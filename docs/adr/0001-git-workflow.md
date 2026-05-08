# Trunk-based workflow with submodule-per-project abstraction

The orchestrator uses a single `main` branch with no feature branches. Each project lives as a git submodule under `src/<repo-name>` and owns its own internal branch strategy. This means the orchestrator's branching complexity is zero — submodules are the abstraction layer that would otherwise require branches.

## Considered options

- **Feature branches per task** — rejected: submodules already provide per-project isolation; adding branches inside the orchestrator creates redundant abstraction with no auditability benefit at this scale
- **Monorepo with all project code inline** — rejected: projects have independent deployment cycles, separate remotes, and must be independently versioned

## Consequences

- Submodule URL changes require updating `.gitmodules` and re-running `git submodule sync`
- All orchestrator commits must be atomic and meaningful — `git log` on `main` is the authoritative history
- Commit order with nested submodules is innermost-first: inner sub-submodule → project submodule → orchestrator. Reversing the order produces redundant pointer-update commits.
