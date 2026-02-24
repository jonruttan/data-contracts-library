# Run Review Workflow Bundle Contract

## Purpose

Run a review using a pre-rendered prompt and optional project vars, then emit a
canonical snapshot.

## Endpoint

- Method: `POST`
- Path: `/review-workflow/run`
- Content-Type: `application/json`
- Idempotent: `false`

## Request

```json
{
  "bundle_path": "payloads/data-contracts-library/review",
  "prompt_id": "adoption_7_personas",
  "prompt_vars": {
    "project": {
      "name": "data-contracts",
      "owner": "data-contracts team",
      "repo_path": "/abs/path/to/data-contracts"
    },
    "runner_lane": "discovery"
  },
  "snapshot_out": "docs/reviews/snapshots/run.adoption-{{date}}.md",
  "runner_lane": "discovery",
  "vars_file": "project_vars.yaml",
  "var_overrides": {
    "context.check_commands.governance[0]": "dc-runner governance"
  }
}
```

## Response

```json
{
  "status": "completed",
  "snapshot_out": "docs/reviews/snapshots/run.adoption-{{date}}.md",
  "rendered_prompt": "rendered_prompts/adoption_7_personas.md",
  "snapshot_template": "/specs/07_runner_behavior/review_workflow/templates/review_snapshot.spec.md",
  "runner_lane": "discovery",
  "runner": "auto",
  "checks": [
    "critical-gate",
    "governance",
    "docs-generate-check"
  ]
}
```

## Error Contract

- Unknown or missing vars file: `400`.
- Variable merge conflict (invalid overrides): `409`.
- Missing required contract variables: `400`.
- Missing `prompt_id` / template mismatch: `404`.
- Runner execution failure: non-zero status with captured command logs.

## Resolution Precedence

1. `vars_file`
2. `prompt_vars`
3. `var_overrides`
4. runner defaults

## Contract Baseline Requirements

Snapshots produced by this flow must pass:

- `/specs/01_schema/review_snapshot_schema_v1.yaml`
- `/specs/02_contracts/26_review_output_contract.md`
