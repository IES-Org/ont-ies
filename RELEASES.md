# IES Composite Releases

This document tracks composite releases of the IES ontology—coordinated releases where multiple modules have been tested together for interoperability.

## About Composite Releases

While individual IES modules are versioned and released independently, composite releases document specific combinations of module versions that have been validated to work together. These are useful when organisations want to adopt a known-good set of modules.

Composite releases are tagged in Git using the format: `ies-release-{yyyy.mm}`

---

## Current Composite Releases

*No composite releases yet. This section will be updated as multiple modules are published and tested together.*

---

## Release History

### Planned

- **ies-release-2025.xx** — First composite release (TBC)
  - IES Common v5.0.0
  - Additional modules as they become available

---

## Individual Module Versions

For the changelog of individual modules, see:

- [IES Common Changelog](docs/common/CHANGELOG.md)

---

## Versioning Strategy

### Module Versioning

Each module follows [Semantic Versioning](https://semver.org/):

- **MAJOR** — Incompatible changes (removing terms, changing IRIs)
- **MINOR** — Backwards-compatible additions (new terms, properties)
- **PATCH** — Backwards-compatible fixes (labels, annotations, documentation)

### Git Tags

- **Module releases**: `{module-id}/v{version}` (e.g., `common/v5.0.0`)
- **Release candidates**: `{module-id}/v{version}-rcN` (e.g., `common/v5.0.0-rc1`)
- **Composite releases**: `ies-release-{yyyy.mm}` (e.g., `ies-release-2025.06`)

### Maintenance Branches

When critical fixes need to be backported to older major versions, maintenance branches are created:

- Format: `{module-id}/v{major}.x` (e.g., `common/v4.x`)
- Created only when needed ("lazy" branching strategy)

---

*© Crown Copyright 2020-2025*
