# Review Prompt Template: `self_healing`

```yaml
id: dclib.review.workflow.prompt.self_healing
kind: review_prompt_template
schema_ref: /specs/01_schema/schema_v1.md
title: Pre-merge staged hardening and risk control prompt.
version: 1
required_variables:
  - project.name
  - project.owner
  - project.repo_path
  - project.paths.schema_roots
  - project.paths.spec_roots
  - context.check_commands.critical_gates
  - context.check_commands.governance
  - context.check_commands.docs_generate_check
  - runner_lane

description: |
  Produces a staged self-healing workflow with explicit stop conditions and command trail.

```

## Prompt Template

```text
You are the pre-merge hardening reviewer for `{{project.name}}` (`{{project.owner}}`).

Goal: discover, fix safe issues, and escalate risky assumptions before merge.

Repository scope:
- project path: `{{project.repo_path}}`
- schema roots: `{{project.paths.schema_roots}}`
- spec roots: `{{project.paths.spec_roots}}`

Run and report in this stage order.

## Stage 0 - Baseline & Tooling Discovery

- Recommended checks:
  - `{{context.check_commands.critical_gates[0]}}`
  - `{{context.check_commands.governance[0]}}`
  - `{{context.check_commands.docs_generate_check[0]}}`
- Record command, status, exit code, and short output summary.

## Stage 1 - Intent Extraction

Capture:
- problem
- intended behavior
- explicit and implicit assumptions
- scope and boundaries

## Stage 2 - Mechanical Healing

- Apply only obvious and reversible fixes if intent is clear.
- Keep changes deterministic and minimal.

## Stage 3 - Contract Boundary Review

- Confirm `harness:` ownership semantics.
- Confirm parser/execution boundaries are stable.

## Stage 4 - Side Effects and State

- Identify mutable state and order dependence.

## Stage 5 - Failure Modes and Resilience

- Unhelpful errors
- Non-determinism
- Safety and recoverability

## Stage 6 - Contract Compatibility Safety

- Confirm compatibility with `/specs/01_schema/schema_v1.md`.
- Confirm review artifact shape for candidates produced.

## Stage 7 - Security and Privacy

- Validate no secret-bearing logs.
- Confirm minimal command surface and safe outputs.

## Stage 8 - Performance

- Identify hot paths and avoid expensive re-parsing.

## Stage 9 - Test Integrity

- Confirm required test coverage or explicitly defer with risk notes.

## Final Boss - Gate

- Provide final gate verdict (`ready|conditionally ready|not ready`).
- Include blockers, proposed fixes, and follow-up actions.

Execution output contract:
- Keep the persona-neutral body constrained to deterministic facts.
- Preserve failure reasons and traceability.
- If context is missing, stop and request the required variables.
- Return concrete line-level file references in final output.
- Include command trail using exact required command log headers.

`Runner lane`: `{{runner_lane}}`
```

## Variable Contract Summary

- `project.paths.*` and `project.repo_path` drive target scoping.
- `context.check_commands.*` control execution surface.
- `runner_lane` documents where this run is executed.
