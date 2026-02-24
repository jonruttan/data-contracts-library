# Render Review Prompt Endpoint Contract

## Purpose

Render a review prompt template from a prompt ID using project variables.

## Endpoint

- Method: `POST`
- Path: `/review-workflow/prompts/{prompt_id}/render`
- Content-Type: `application/json`
- Idempotent: `true`

## Request

```json
{
  "prompt_id": "adoption_7_personas",
  "prompt_vars": {
    "project": {
      "name": "data-contracts",
      "owner": "data-contracts team",
      "repo_path": "/abs/path/to/data-contracts",
      "reviewer_bundle_id": "data-contracts-library-review-workflow",
      "paths": {
        "schema_roots": ["/specs/01_schema"],
        "spec_roots": ["/specs"],
        "contract_roots": ["/specs/02_contracts"]
      }
    },
    "context": {
      "check_commands": {
        "critical_gates": ["dc-runner critical-gate"],
        "governance": ["dc-runner governance"],
        "docs_generate_check": ["dc-runner docs-generate-check"]
      }
    },
    "runner_lane": "governance"
  }
}
```

`prompt_vars` may be either inline map or YAML/JSON file path when available.

Supported override source order:

1. base vars YAML file
2. CLI key/value overrides (`--var key=value`)
3. caller-supplied defaults

## Response

```json
{
  "prompt_id": "adoption_7_personas",
  "rendered_prompt_path": "rendered_prompts/adoption_7_personas.md",
  "template_ref": "/specs/07_runner_behavior/review_workflow/prompts/adoption_7_personas.spec.md",
  "unresolved_keys": [],
  "snapshot_seed_path": "rendered_prompts/review_snapshot_template.md"
}
```

## Error Contract

- Missing required variable keys: `400` with missing-key list.
- Unknown variable keys: `400` with warning/ignore policy and explicit key list.
- Prompt id not found: `404` with allowed IDs.
- Render failure: `422` with template parse details.

## Canonical Sources

- `/specs/07_runner_behavior/review_workflow/prompts/*.spec.md`
- `/specs/07_runner_behavior/review_workflow/review_variables.schema.md`
