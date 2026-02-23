# Repo Migration Map

This map records hard-cut migration into `data-contracts-library`.

## Repository Migrations

| Source Repository | Status | Destination Root |
|---|---|---|
| `data-contracts-bundle-spec` | migrated | `/specs/05_libraries/bundle_tooling/**`, `/specs/01_schema/**`, `/specs/02_contracts/**` |
| `data-contracts-bundler-spec` | migrated | `/specs/05_libraries/bundle_tooling/**`, `/specs/01_schema/**`, `/specs/02_contracts/**` |

## Path Mapping

| Old Path | New Path |
|---|---|
| `data-contracts-bundle-spec/specs/schema/**` | `data-contracts-library/specs/01_schema/**` |
| `data-contracts-bundle-spec/specs/contract/**` | `data-contracts-library/specs/02_contracts/**` |
| `data-contracts-bundle-spec/fixtures/**` | `data-contracts-library/specs/05_libraries/bundle_tooling/fixtures/bundle_spec/**` |
| `data-contracts-bundle-spec/bundles/**` | `data-contracts-library/specs/05_libraries/bundle_tooling/bundles/**` |
| `data-contracts-bundler-spec/specs/schema/**` | `data-contracts-library/specs/01_schema/**` |
| `data-contracts-bundler-spec/specs/contract/**` | `data-contracts-library/specs/02_contracts/**` |
| `data-contracts-bundler-spec/specs/fixtures/**` | `data-contracts-library/specs/05_libraries/bundle_tooling/fixtures/bundler_spec/**` |

## Bundle IDs (Canonical)

- `data-contracts-library-core`
- `data-contracts-runner-shared-behavior`
- `data-contracts-library-overlays`
- `data-contracts-library-bundle-tooling`
