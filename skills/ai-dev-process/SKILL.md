---
name: ai-dev-process
description: Orchestrate an AI-assisted development workflow by tracking the current phase, reconciling artifacts, and proposing the next collaborative step. Use when the user wants to bootstrap or resume a structured dev workflow, track progress in devprocess.md, or coordinate grill-me, to-prd, to-issues, triage, and tdd.
---

# AI Dev Process

Track and steer a project's AI-assisted development process through a persistent `devprocess.md` file.

## Quick start

When invoked:

1. Check for `devprocess.md`.
2. If missing, create it from [DEVPROCESS-TEMPLATE.md](DEVPROCESS-TEMPLATE.md).
3. Propose the default layout from [REFERENCE.md](REFERENCE.md) and ask the user to confirm or override it.
4. Reconcile `devprocess.md` with the filesystem and issue tracker state if available.
5. Tell the user:
   - what is complete
   - the current `NEXT_PHASE`
   - the current `NEXT_ACTION`
   - what you propose to do now
6. Ask: **“Shall we proceed?”**

## Workflows

### Resume or steer the process

- Treat `devprocess.md` as the canonical tracker.
- Keep exactly one `NEXT_PHASE` and one `NEXT_ACTION`.
- Use the workflow log to record transitions, blockers, corrections, and key decisions.
- If tracker and reality disagree, raise the inconsistency and resolve it with the user before changing direction.
- After a phase completes, update `devprocess.md`, summarize what finished, announce what is next, and ask for confirmation.

### Apply the right companion skill

Follow the phase mapping in [REFERENCE.md](REFERENCE.md).

When a phase requires a companion skill, explicitly switch into that skill's workflow if available locally. Do not merely mention the skill by name. If it is not available locally, advise the user to clone the companion skills repository, explicitly say that this workflow cannot proceed as intended without those companion skills, offer to help them do that, and then load the required skills once available.

## Advanced features

See [REFERENCE.md](REFERENCE.md) for:

- default phases
- companion skill mapping
- completion criteria
- reconciliation rules
- post-phase behavior
