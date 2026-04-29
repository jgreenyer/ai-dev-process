# ai-dev-process

A reusable skill for orchestrating an AI-assisted development workflow.

## What it does

The `ai-dev-process` skill tracks progress in a persistent `devprocess.md`, reconciles that tracker with repo reality, and proposes the next collaborative step for the agent and developer.

It is designed to work with companion skills from Matt Pocock's `skills` repository:

- https://github.com/mattpocock/skills/tree/main/skills

`ai-dev-process` is explicitly inspired by Matt Pocock's skill system and is intended to orchestrate and use skills from that repository. In particular, this skill builds on the workflow style and companion skills authored by Matt Pocock.

Especially:

- `grill-me`
- `to-prd`
- `to-issues`
- `triage`
- `tdd`

## Repository layout

- `skills/ai-dev-process/SKILL.md` — skill definition
- `skills/ai-dev-process/DEVPROCESS-TEMPLATE.md` — default `devprocess.md` template

## Default tracked workflow

1. **Prompt Spec**: Describe the intention and define mocks. Store any supporting artifacts in `spec/` and the main spec in `spec/spec.md`.
2. **Grill me -> Requirements Specification** *(use `grill-me`, then `to-prd`)*: Stress-test the idea and generate a requirements specification in `PRD.md`.
3. **Derive Issues/Stories** *(use `to-issues`)*: Extract issues/stories and store them in `issues/needs-triage`, or create GitHub issues if a GitHub project is linked, initially marked as `needs-triage`.
4. **Select Core Stories**: Choose the key stories for prototyping first.
5. **Architecture Definition** *(use `grill-me`)*: Using prompts or interactive sessions, define the architecture and folder/package structure, and store the result in `design.md`.
6. **Incremental Implementation & Workflow Management** *(use `triage`)*: Triage issues first and route them to `needs-info`, `ready-for-agent`, `ready-for-human`, or `wontfix`. Once an issue is `ready-for-agent`, move it through the implementation flow such as `todo -> in-progress -> review -> done`.
   - **Use SDD (Specification-Driven Development)**: First define the functionality specification, ideally including a Mermaid diagram showing how the solution integrates into the existing architecture, and attach that to the in-progress issue.
   - **Use TDD (Test-Driven Development)** *(use `tdd`)*: Implement the stories using TDD.
   - **Maintain Design**: If difficulties arise or refactoring leads to design changes, update `design.md` accordingly.

## Why use this process?

Compared to ad-hoc "vibe coding", this process makes AI-assisted development more deliberate, inspectable, and recoverable.

- It turns vague intent into durable artifacts such as `spec/spec.md`, `PRD.md`, and `design.md`.
- It keeps developer and agent aligned on what is currently being done and what should happen next.
- It breaks large ideas into triaged, actionable stories instead of jumping straight into implementation.
- It encourages specification and testing before code, reducing thrash and accidental complexity.
- It makes backtracking explicit by recording changes in `devprocess.md` rather than silently changing direction.
- It supports resuming work later, because the current phase, next action, and workflow history are persisted.

The goal is not to remove iteration, but to give iteration structure so that exploration remains understandable and implementation stays connected to intent.

## Author

Joel Greenyer  
Fachgebiet Software Engineering  
Universität Kassel  
joel.greenyer@uni-kassel.de

## Acknowledgements

This project honors Matt Pocock, author of the `skills` repository, whose work inspired this skill and whose companion skills are intended to be used with it:

- Matt Pocock's `skills` repository: https://github.com/mattpocock/skills/tree/main/skills

## License

MIT
