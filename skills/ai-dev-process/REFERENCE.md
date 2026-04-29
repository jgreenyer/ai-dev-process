# Reference

## Default layout

- `devprocess.md` — process tracker
- `spec/spec.md` — prompt spec
- `spec/` — mocks and supporting artifacts
- `PRD.md` — requirements specification
- `design.md` — architecture/design
- `issues/needs-triage/` — local issue store when GitHub is not linked

Ask once whether to accept or override this layout. If overridden, record the custom layout in `devprocess.md`.

## Default phases

1. `prompt-spec`
2. `requirements-specification`
3. `derive-issues-stories`
4. `select-core-stories`
5. `architecture-definition`
6. `incremental-implementation-workflow-management`

## Companion skills

This skill is inspired by Matt Pocock's skill system and is intended to orchestrate companion skills from:

- `https://github.com/mattpocock/skills/tree/main/skills`

When the required companion skill is available locally, explicitly switch into that workflow. Do not merely mention it.

Required phase behavior:

- `prompt-spec` -> create `spec/spec.md` and any needed files under `spec/`
- `requirements-specification` -> apply `grill-me`, then apply `to-prd`
- `derive-issues-stories` -> apply `to-issues`
- `architecture-definition` -> apply `grill-me`, then update `design.md`
- `incremental-implementation-workflow-management` -> apply `triage` for issue flow and `tdd` for implementation work

If a required companion skill is unavailable locally, say so explicitly, point the user to the expected source repository, and advise them to clone it:

- `https://github.com/mattpocock/skills/tree/main/skills`

Offer to help the user clone or install that repository locally. Explicitly state that the workflow cannot proceed as intended without those companion skills being available locally. Once the companion skills are available locally, load and apply the required skills. If the user does not want to do that, continue manually using the same workflow shape, while making clear that this is a fallback rather than the intended workflow.

## Completion criteria

Use these defaults unless the user specifies otherwise:

- `prompt-spec`: `spec/spec.md` exists and the intent/mocks are captured
- `requirements-specification`: `PRD.md` exists and reflects grilled requirements
- `derive-issues-stories`: issues exist locally or in GitHub and start in `needs-triage`
- `select-core-stories`: prototype stories are explicitly identified
- `architecture-definition`: `design.md` exists and matches current understanding
- `incremental-implementation-workflow-management`: at least one issue is actively flowing through triage/spec/TDD/review

## Reconciliation rules

- Treat `devprocess.md` as canonical, but reconcile it with repo artifacts and issue tracker state.
- Keep exactly one `NEXT_PHASE` and one `NEXT_ACTION`.
- If tracker and reality disagree, do not silently rewrite state. Raise the inconsistency, explain it, and resolve it with the user.
- Backtracking is allowed by changing `NEXT_*` and logging why.

## After each completed phase

1. Update `devprocess.md`
2. Summarize what finished
3. State the new `NEXT_PHASE`
4. State the new `NEXT_ACTION`
5. Propose the next collaborative step
6. Ask: **“Shall we proceed?”**
