# Review Workflow Canonical Assets

Canonical project-agnostic review workflow source for rendering prompts and review snapshots.

## Assets

- `/specs/07_runner_behavior/review_workflow/prompts/adoption_7_personas.spec.md`
- `/specs/07_runner_behavior/review_workflow/prompts/self_healing.spec.md`
- `/specs/07_runner_behavior/review_workflow/templates/review_snapshot.spec.md`
- `/specs/07_runner_behavior/review_workflow/endpoints/render_prompt.spec.md`
- `/specs/07_runner_behavior/review_workflow/endpoints/run_review_bundle.spec.md`
- `/specs/07_runner_behavior/review_workflow/review_variables.schema.md`

## Canonical Flow

1. Provide project variables via YAML vars file and optional CLI overrides.
2. Resolve the active prompt template.
3. Render prompt text with bound variables.
4. Execute a review run using selected `runner_lane`.
5. Emit snapshot content from the canonical snapshot template.

## Ownership Model

- Prompt and template content lives here as reusable assets.
- Runtime execution, rendering engine, transport endpoints, and bundle consumers are owned by runner tooling.
