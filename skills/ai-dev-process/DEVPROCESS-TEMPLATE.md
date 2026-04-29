# devprocess.md

Use this as the default project tracker for the AI-assisted development process.

```md
# Development Process

## Process Definition

1. Prompt Spec: Describe the intention and define mocks (store any artifacts in the `spec/` folder if needed).
2. Grill me -> Requirements Specification (use `grill-me`, then `to-prd`): Stress-test the idea and generate a requirements specification (`PRD.md`).
3. Derive Issues/Stories (use `to-issues`): Extract issues/stories and store them in `issues/needs-triage`, or create GitHub issues initially marked as `needs-triage`.
4. Select Core Stories: Choose key stories for prototyping.
5. Architecture Definition (use `grill-me`): Define the architecture and folder/package structure (store in `design.md`).
6. Incremental Implementation & Workflow Management (use `triage`): Triage issues first and route them to `needs-info`, `ready-for-agent`, `ready-for-human`, or `wontfix`. Once an issue is ready-for-agent, move it into the implementation flow, e.g. `todo -> in-progress -> review -> done`.
   - Use SDD (Specification-Driven Development): First define the functionality specification, ideally including a Mermaid diagram showing how the solution integrates into the existing architecture (attach to the issue while it is in-progress).
   - Use TDD (Test-Driven Development) (use `tdd`): Implement the stories using TDD.
   - Maintain Design: If difficulties arise or refactoring leads to design changes, update `design.md` accordingly.

## Project Layout

- `devprocess.md` - process tracker
- `spec/spec.md` - prompt spec
- `spec/` - mocks and supporting artifacts
- `PRD.md` - requirements specification
- `design.md` - architecture/design
- `issues/needs-triage/` - local issue store when GitHub is not linked

## Current State

NEXT_PHASE: prompt-spec
NEXT_ACTION: Work with the developer to create `spec/spec.md` and capture any mocks or supporting artifacts under `spec/`.

## Current Summary

COMPLETED:
- None yet.

IN_PROGRESS:
- Project bootstrap.

BLOCKERS:
- None recorded.

OPEN_QUESTIONS:
- Confirm whether the default project layout should be used or overridden.

## Workflow Log

- [bootstrap] Initialized development process tracker. Set `NEXT_PHASE` to `prompt-spec`.

## Guidance for the Agent

- Treat `NEXT_PHASE` and `NEXT_ACTION` as canonical.
- Before changing them, reconcile this file with actual repo artifacts and issue tracker state if available.
- If reality and this file disagree, raise the inconsistency to the user and resolve it collaboratively.
- After a phase is completed, update this file, summarize what finished, announce the next step, and ask: "Shall we proceed?"
```

## Notes

- Keep exactly one `NEXT_PHASE` and one `NEXT_ACTION`.
- Backtracking is allowed by changing `NEXT_*` and logging the reason in `Workflow Log`.
- Prefer updating history and summary instead of inventing extra state markers.
