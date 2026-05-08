# Standard HOOTL/HITLFE/HIC task classification for AI agents

AI agents operating in the orchestrator classify every task node as `[HOOTL]`, `[HITLFE]`, or `[HIC]` before acting. This governs when an agent proceeds autonomously versus pausing for human input.

## Decision

Three-tier classification:

- **`[HOOTL]`** — AI executes autonomously; human audits after-the-fact. High confidence, deterministic outcome. Agent executes without prompting.
- **`[HITLFE]`** — AI handles routine prep, escalates exception to human for approval. Agent completes all prep work first, then pauses with a structured context summary (what was done, why input is needed, potential impact) before proceeding.
- **`[HIC]`** — Human-in-Command. Task requires creativity, judgment, or empathy that AI cannot substitute. Agent surfaces the task and waits.

Agents follow Prepare-Then-Prompt: no asking permission before acting on `[HOOTL]` tasks. Multiple `[HITLFE]` and `[HIC]` items are batched into a single daily briefing rather than scattered interrupts.

## Considered options

- **Interrupt-on-uncertainty** — ask the human whenever confidence drops below a threshold, without doing prep work first. Rejected: creates constant low-signal interrupts and shifts cognitive load onto the human before they have enough context to decide.
- **Fully autonomous with human review after** — agent completes everything, human reviews in post. Rejected: too late to catch high-stakes or hard-to-reverse actions mid-flight; removes meaningful human control over consequential steps.
- **Explicit per-task approval prompts before every action** — rejected: high friction, trains users to click through without reading, and collapses `[HOOTL]` and `[HITLFE]` into one noisy mode.

## Consequences

- Agents must tag each task node at planning time; ambiguous tasks should default to `[HITLFE]` rather than `[HOOTL]`.
- The daily briefing pattern requires that agents track which tasks pended human input across a session and surface them together at natural stopping points.
- This classification is an orchestrator-level convention; project submodules may adopt it internally but are not required to.
