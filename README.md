# ai-dev-process

A reusable skill for orchestrating an AI-assisted development workflow.

## What it does

The `ai-dev-process` skill tracks progress in a persistent `devprocess.md`, reconciles that tracker with repo reality, and proposes the next collaborative step for the agent and developer.

It is designed to work with companion skills from:

- https://github.com/mattpocock/skills/tree/main/skills

This skill repo is built in appreciation of Matt Pocock's `skills` repository, whose structure and companion workflows inspired this meta-skill. If you use `ai-dev-process`, you should also look at Matt Pocock's skills and credit that work where appropriate.

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

1. Prompt Spec
2. Requirements Specification
3. Derive Issues/Stories
4. Select Core Stories
5. Architecture Definition
6. Incremental Implementation & Workflow Management

## Author

Joel Greenyer  
Fachgebiet Software Engineering  
Universität Kassel  
joel.greenyer@uni-kassel.de

## Acknowledgements

Honoring inspiration and companion workflow design from Matt Pocock's skills repository:

- https://github.com/mattpocock/skills/tree/main/skills

## License

MIT
