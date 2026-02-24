# Bundler CLI Contract (v1)

## Canonical Command Surface

- `bundle resolve`
  - deterministic dependency closure over canonical manifests
  - emits reproducible `resolved_bundle_lock_v1.yaml` and `resolved_files.sha256`
- `bundle package`
  - packages resolved payload into a canonical tarball plus checksum and attestation metadata
- `bundle package-check`
  - validates package integrity from `.sha256` sidecar
- `bundle list [--json]`
  - enumerate canonical bundles
- `bundle info --bundle-id <bundle_id> [--json]`
  - inspect canonical bundle metadata
- `bundle install --project-lock <path> --out <dir>`
  - installs bundles from pinned `project_bundle_lock_v1.yaml`
  - verifies package SHA256 from lock `source.sha256`
  - verifies unpacked `resolved_bundle_lock_v1.yaml`
  - verifies unpacked `resolved_files.sha256` payload checksums
- `bundle install-check --project-lock <path> --out <dir>`
  - re-verifies installed payload bytes against lock + manifest
  - validates drift safety before reuse
- `bundle bootstrap --lock <path> --out <dir> [--force-bootstrap]`
  - one-time ad-hoc bootstrap for self-governed tool installation
  - bootstrap lock MUST contain exactly one bundle entry
  - bootstrap bundle id MUST equal `data-contracts-bundler`
  - requires explicit `--force-bootstrap` if `.bundler/bootstrap.state.json` exists
- `bundle bootstrap-check --state <path>`
  - validates bootstrap marker schema, installed path, and payload integrity
- `bundle outdated --project-lock <path> [--format text|json]`
  - compares pinned versions to canonical manifest versions
- `bundle upgrade --project-lock <path> [--bundle-id <id>...] [--to <version|latest>] [--out <path|stdout>] [--dry-run|--write-lock] [--allow-major]`
  - computes deterministic upgrade plans per bundle
  - major version updates are blocked unless `--allow-major`
  - defaults to non-destructive dry-run
  - writes lock only with `--write-lock` and explicit output mode

## Post-Bootstrap Invariant

Normal install/install-check flows MUST use pinned lock metadata only and MUST NOT accept unguided ad-hoc source inputs.

## Error Contract

Errors MUST be direct and actionable, including:

- invalid lock shape
- missing or invalid source bytes
- checksum mismatch
- install directory overlap
- bootstrap marker reuse without force
- major version drift rejection (unless explicit)
- manifest drift in install/check
