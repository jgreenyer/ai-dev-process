---
name: ai-dev-process
description: Orchestrate an AI-assisted development workflow by tracking the current phase, reconciling artifacts, and proposing the next collaborative step. Use when the user wants to manage a dev process, bootstrap or resume a project workflow, track progress in devprocess.md, or coordinate grill-me, to-prd, to-issues, triage, and tdd.
---

# AI Dev Process

Track and steer the project's development process through a persistent `devprocess.md` file.

## Quick start

When invoked:

1. Check for `devprocess.md`.
2. If missing, create it from [DEVPROCESS-TEMPLATE.md](DEVPROCESS-TEMPLATE.md).
3. Propose the default layout and ask the user to confirm or override it:
   - `devprocess.md`
   - `spec/spec.md`
   - `spec/`
   - `PRD.md`
   - `design.md`
   - `issues/needs-triage/`
4. Reconcile `devprocess.md` with the filesystem and issue tracker state if available.
5. Tell the user:
   - what is complete
   - what the current `NEXT_PHASE` is
   - what the current `NEXT_ACTION` is
   - what you propose to do now
6. Ask: **“Shall we proceed?”**

## Rules

- Treat `devprocess.md` as the canonical tracker.
- The tracker must always contain exactly one `NEXT_PHASE` and one `NEXT_ACTION`.
- Use the workflow log to record transitions, corrections, blockers, and key decisions.
- Backtracking is implicit: set `NEXT_*` to an earlier phase and log why.
- If tracker and reality disagree, do **not** silently rewrite state. Raise the inconsistency, explain it, and drive to a shared understanding first.
- After completing a phase, update `devprocess.md`, summarize what finished, state what is next, propose the next collaborative action, and ask for confirmation.

## Default phases

1. `prompt-spec`
2. `requirements-specification`
3. `derive-issues-stories`
4. `select-core-stories`
5. `architecture-definition`
6. `incremental-implementation-workflow-management`

## Orchestration

The referenced skills are expected to come from this skills repository:

- `https://github.com/mattpocock/skills/tree/main/skills`

When a phase calls for another skill, prefer delegating to it:

- `prompt-spec` -> work with the user to create `spec/spec.md` and any files under `spec/`
- `requirements-specification` -> use `grill-me`, then `to-prd`
- `derive-issues-stories` -> use `to-issues`
- `architecture-definition` -> use `grill-me`, then update `design.md`
- `incremental-implementation-workflow-management` -> use `triage` for issue flow and `tdd` for implementation

If a referenced skill is unavailable locally, mention that the expected companion skills live in `mattpocock/skills`, explain the intended workflow, and continue manually.

## Completion criteria by phase

Use these as defaults and confirm with the user when ambiguous:

- `prompt-spec`: `spec/spec.md` exists and the intent/mocks are captured
- `requirements-specification`: `PRD.md` exists and reflects grilled requirements
- `derive-issues-stories`: issues exist locally or in GitHub and start in `needs-triage`
- `select-core-stories`: prototype stories are explicitly identified
- `architecture-definition`: `design.md` exists and matches current understanding
- `incremental-implementation-workflow-management`: at least one issue is actively flowing through triage/spec/TDD/review

## Reference

Use [DEVPROCESS-TEMPLATE.md](DEVPROCESS-TEMPLATE.md) as the default `devprocess.md` format.
