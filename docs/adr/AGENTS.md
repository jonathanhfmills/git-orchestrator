<!-- Parent: docs/AGENTS.md -->

# docs/adr

## Purpose
Architectural Decision Records for the orchestrator. Each file documents a single hard-to-reverse or surprising decision made at the orchestrator level, including the options considered and consequences accepted. ADRs here cover only orchestrator infrastructure concerns (git workflow, commit conventions, task-tracking location); project-level ADRs live inside the respective submodule at `src/<repo>/docs/adr/`.

## Key Files
| File | Description |
|------|-------------|
| `0001-git-workflow.md` | Trunk-based workflow with no feature branches; submodules provide per-project isolation |
| `0002-commit-convention.md` | `tag: Description` commit format (no scope, no footer); tags mirror Daily Log line-item prefixes |
| `0003-task-tracking-in-root.md` | Daily logs and backlog centralised in orchestrator root, not inside submodules |
| `0004-hitl-task-classification.md` | Three-tier HITL classification (`[HOOTL]`, `[HITLFE]`, `[HIC]`) governing when agents proceed vs. pause for human input |
| `0005-submodule-branch-strategy.md` | Sub-submodule branch strategy: feature branch with PR into `main`; no direct pushes to main |
| `0006-local-dev-environment.md` | Local development stack setup and constraints |

## For AI Agents

### Working In This Directory
- ADR files are append-only records of past decisions. Do not edit existing ADRs to reverse a decision — write a new ADR that supersedes the old one and references it.
- Filename pattern: `NNNN-kebab-case-title.md` where `NNNN` is a zero-padded sequence number one higher than the current maximum.
- Each ADR should include: a title, the decision made, options considered (with rejection rationale), and consequences.

### Common Patterns
- Files are plain Markdown with no front matter.
- Decisions are stated as completed facts ("The orchestrator uses…"), not proposals.

<!-- MANUAL: Any manually added notes below this line are preserved on regeneration -->
