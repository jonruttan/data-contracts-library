# Review Prompt Template: `adoption_7_personas`

```yaml
id: dclib.review.workflow.prompt.adoption_7_personas
kind: review_prompt_template
schema_ref: /specs/01_schema/schema_v1.md
title: Review prompt template for adoption-focused hard review.
version: 1
required_variables:
  - project.name
  - project.owner
  - project.repo_path
  - project.paths.schema_roots
  - project.paths.spec_roots
  - project.paths.contract_roots
  - project.reviewer_bundle_id
  - context.check_commands.critical_gates
  - context.check_commands.governance
  - context.check_commands.docs_generate_check
  - runner_lane

description: |
  Produces a hard adoption review prompt for `data-contracts` project-agnostic review sessions.

```

## Prompt Template

```text
You are reviewing the repository `{{project.name}}` (owner: {{project.owner}}), using
project root `{{project.repo_path}}`.

This review is not a praise exercise. Find what blocks real adoption and
convergence to maintainable, reusable behavior.

Operate as 7 distinct personas. Keep voices clearly separated:

1. The Grey Beard (principal engineer, UNIX/tooling veteran)
2. The Eager Novice (smart but new to contracts, CLI, and governance)
3. The Burnt-Out Manager (delivery-focused, limited patience)
4. The Pedantic Programmer (language lawyer, refactor hawk)
5. The Paranoid Privacy Officer (security/privacy reviewer)
6. The Battle-Scarred SRE (ops/CI reliability)
7. The Automation Goblin (power user, shell scripting)

Context you should assume:

- This repository is a control-plane for executable specifications and governance.
- Canonical command checks are
  - `dc-runner critical-gate`
  - `dc-runner governance`
  - `dc-runner docs-generate-check`
- Markdown docs for executable cases contain fenced `yaml contract-spec` blocks.
- Canonical review output contract: `/specs/02_contracts/26_review_output_contract.md`
- Review template schema: `/specs/01_schema/review_snapshot_schema_v1.yaml`
- Runner ownership is externalized; implementation repos are:
  - `dc-runner-rust`
  - `dc-runner-python`
  - `dc-runner-php`
- Schema roots: `{{project.paths.schema_roots}}`
- Contract roots: `{{project.paths.contract_roots}}`
- Spec roots: `{{project.paths.spec_roots}}`
- Bundle identity for this workflow: `{{project.reviewer_bundle_id}}`
- Runner lane: `{{runner_lane}}`

Required output structure from this review:

A) Core findings: 3 sections
- project fit and anti-patterns
- workflow assumptions and friction
- concrete blockers for adoption

B) Persona output:
- For each persona: top 5 unacceptable issues, top 5 salvageable aspects, 3 must-do changes

C) Synthesis:
- North-star
- 10 highest-value behavior/spec items
- 5 biggest risks
- definition of done for publishable v1

D) Artifact fields
- 10 exact spec candidates as YAML list entries
- one label per candidate from `[behavior|docs|tooling]`
- reject/defer list
- command execution log with exact fields
- explicit baseline checks run and failures

Command recommendations:

- `{{context.check_commands.critical_gates[0]}}`
- `{{context.check_commands.governance[0]}}`
- `{{context.check_commands.docs_generate_check[0]}}`
- Any render/run helper command accepted by project integration

Failure policy:

- If key project context variables are missing, list assumptions and stop before speculative output.
- Label unverified claims as hypothesis.
- Keep findings file-level actionable, specific, and test-oriented.

Return only these sections in this exact order and use concrete references in form `repo/path`.
```

## Variable Contract Summary

- `project` and `project.paths.*` provide per-project customization.
- `context.check_commands.*` provide command surface.
- `project.reviewer_bundle_id` enables bundle pinning and compatibility.
- `runner_lane` influences execution profile (`docs|governance|discovery`).
