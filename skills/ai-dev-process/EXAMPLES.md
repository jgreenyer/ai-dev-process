# Examples

## Bootstrap a new project

User asks to start a structured AI-assisted workflow for a fresh idea.

Agent should:

1. Check for `devprocess.md`
2. Create it from `DEVPROCESS-TEMPLATE.md` if missing
3. Propose the default layout
4. Report the initial `NEXT_PHASE` and `NEXT_ACTION`
5. Ask: **"Shall we proceed?"**

## Resume an existing project

User asks where the project is in the process.

Agent should:

1. Read `devprocess.md`
2. Reconcile it with the repo and issue state
3. Report what is complete
4. Report the current `NEXT_PHASE` and `NEXT_ACTION`
5. Raise inconsistencies before proceeding

## Requirements phase

If `NEXT_PHASE` is `requirements-specification`, the agent should explicitly apply:

1. `grill-me`
2. `to-prd`

It should not merely recommend those skills.

## Implementation issue with diagrams

Before TDD on a `ready-for-agent` issue, the agent should:

1. Inspect `design.md`
2. Cross-check the planned issue-level design against it
3. Decide whether SDD and Mermaid diagrams would help
4. If yes, recommend specific diagram types and ask to proceed
5. Use the Mermaid skill if available locally
6. Only then proceed to `tdd`
