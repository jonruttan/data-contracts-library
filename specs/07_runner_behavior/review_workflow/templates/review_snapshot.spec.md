# Review Snapshot Template (Canonical)

```yaml
id: dclib.review.workflow.template.review_snapshot_v1
kind: review_snapshot_template
schema_ref: /specs/01_schema/schema_v1.md
version: 1
requires:
  - /specs/01_schema/review_snapshot_schema_v1.yaml
  - /specs/02_contracts/26_review_output_contract.md
required_sections:
  - Scope Notes
  - Command Execution Log
  - Findings
  - Synthesis
  - Spec Candidates (YAML)
  - Classification Labels
  - Reject / Defer List
  - Raw Output
```

```text
# Review Snapshot

Date: {{run.date}}
Model: {{run.model}}
Prompt: `{{run.prompt_path}}`
Prompt revision: {{run.prompt_revision}}
Repo revision: {{run.repo_revision}}
Contract baseline refs:
- /specs/01_schema/review_snapshot_schema_v1.yaml
- /specs/02_contracts/26_review_output_contract.md
Runner lane: {{run.runner_lane}}

## Scope Notes
- {{run.scope_summary}}
- {{run.review_focus}}
- {{run.check_summary}}

## Command Execution Log

| command | status | exit_code | stdout_stderr_summary |
| --- | --- | --- | --- |
| `<command>` | success \| failure \| skipped | <exit code or "-"> | <short summary> |

## Findings

| Severity | Verified/Hypothesis | File:Line | What | Why | When | Proposed fix |
| --- | --- | --- | --- | --- | --- | --- |
| High | Hypothesis | - | Add first finding row with this exact schema | Why is this relevant to review scope? | during review | Concrete follow-up action |

## Synthesis

- North-star: {{run.north_star}}
- 10 highest-value spec items:
  - {{run.spec_item_1}}
  - {{run.spec_item_2}}
  - {{run.spec_item_3}}
  - {{run.spec_item_4}}
  - {{run.spec_item_5}}
  - {{run.spec_item_6}}
  - {{run.spec_item_7}}
  - {{run.spec_item_8}}
  - {{run.spec_item_9}}
  - {{run.spec_item_10}}
- 5 biggest risks:
  - {{run.risk_1}}
  - {{run.risk_2}}
  - {{run.risk_3}}
  - {{run.risk_4}}
  - {{run.risk_5}}
- Definition of done:
  - {{run.definition_of_done}}

## Spec Candidates (YAML)

```yaml
- id: DOCS-REV-0001
  title: Example candidate
  type: docs
  class: docs
  target_area: path/to/target
  acceptance_criteria:
    - "Replace with concrete acceptance criteria."
    - "Populate affected paths and risk."
  affected_paths:
    - path/to/target
  risk: medium
```

## Classification Labels

- DOCS-REV-0001: docs

## Reject / Defer List

- {{run.reject_item_1}}
- {{run.reject_item_2}}
- {{run.reject_item_3}}
- {{run.reject_item_4}}
- {{run.reject_item_5}}

## Raw Output

Paste the full AI output here. Do not edit beyond formatting fixes.
```

## Notes

- This is a canonical markdown-only artifact scaffold for review snapshots.
- Keep required section order and heading names unchanged.
- All values may be templated before render.
