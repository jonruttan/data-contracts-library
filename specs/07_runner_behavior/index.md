# Runner Behavior

Canonical reusable runner-behavior surfaces for the `data-contracts` ecosystem are split by ownership:

- Shared behavior authored in `data-contracts-runner`.
- Shared reusable libraries and overlays in `data-contracts-library`.
- Canonical review workflow assets in this repository subtree:
  - `/specs/07_runner_behavior/review_workflow/index.md`
  - `/specs/07_runner_behavior/review_workflow/prompts/*`
  - `/specs/07_runner_behavior/review_workflow/templates/*`
  - `/specs/07_runner_behavior/review_workflow/endpoints/*`
  - `/specs/07_runner_behavior/review_workflow/review_variables.schema.md`

Implementation-specific runner behavior remains external:

- `dc-runner-rust`
- `dc-runner-python`
- `dc-runner-php`
- `data-contracts-runner`
