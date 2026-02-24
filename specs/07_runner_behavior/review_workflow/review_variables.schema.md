# Review Workflow Variable Contract (Canonical)

version: 1
id: data-contracts-library.review_workflow.variables
required: [project, context, runner_lane]

properties:
  project:
    type: object
    required:
      - name
      - owner
      - repo_path
      - reviewer_bundle_id
      - paths
    properties:
      name:
        type: string
      owner:
        type: string
      repo_path:
        type: string
      reviewer_bundle_id:
        type: string
      paths:
        type: object
        required:
          - schema_roots
          - spec_roots
          - contract_roots
        properties:
          schema_roots:
            type: array
            items:
              type: string
          spec_roots:
            type: array
            items:
              type: string
          contract_roots:
            type: array
            items:
              type: string
  context:
    type: object
    required:
      - check_commands
    properties:
      check_commands:
        type: object
        required:
          - critical_gates
          - governance
          - docs_generate_check
        properties:
          critical_gates:
            type: array
            items:
              type: string
          governance:
            type: array
            items:
              type: string
          docs_generate_check:
            type: array
            items:
              type: string
  run:
    type: object
    properties:
      snapshot_template:
        type: string
      runner:
        type: string
      bundle_path:
        type: string
      output_path:
        type: string
  runner_lane:
    type: string
    enum: [docs, governance, discovery]

variables:
  - key: project.name
    description: Display/project identifier.
  - key: project.owner
    description: Owning team or user for traceability.
  - key: project.repo_path
    description: Repository-relative or absolute path to reviewed repo.
  - key: project.reviewer_bundle_id
    description: Bundle identity for review assets.
  - key: project.paths.schema_roots
    description: Schema lookup roots, for example ["/specs/01_schema"]
  - key: project.paths.spec_roots
    description: Executable spec roots, for example ["/specs"]
  - key: project.paths.contract_roots
    description: Contract roots, for example ["/specs/02_contracts"]
  - key: context.check_commands.critical_gates
    description: Ordered command list for critical checks.
  - key: context.check_commands.governance
    description: Ordered command list for governance checks.
  - key: context.check_commands.docs_generate_check
    description: Ordered command list for documentation checks.
  - key: runner_lane
    description: Execution lane for the review run.
  - key: project.paths
    description: Structured path object used for schema/template discovery.

notes:
  - Values are merged from a YAML vars file and CLI `--var key=value` overrides.
  - Unknown keys are rejected with actionable diagnostics.
  - Missing required keys fail fast before render.
