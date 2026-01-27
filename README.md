# Information Exchange Standard (IES)  

**Repository:** `ont-ies`  
**Description:** The home of the UK Government's Information Exchange Standard, enabling consistent and open data exchange across domains.  

<!--  
SPDX-License-Identifier: See individual files for license.  
- Source code: MIT  
- Documentation: OGL-UK-3.0  
-->  

## Overview  

The **Information Exchange Standard (IES)** is a UK Government initiative to support consistent, open, and interoperable data exchange. It provides a shared semantic foundation that enables public sector organisations to collaborate and integrate systems more effectively.  

The standard is designed to be modular and extensible, with support for evolving domain-specific extensions led by diverse teams across government.  

This repository is the official home of IES and includes documentation, example data, and ontology models to support adoption and use.  

---  

## Repository Structure

This repository is organised to support multiple IES ontology modules:

```
ont-ies/
├── docs/
│   ├── index.md              # Documentation landing page
│   ├── glossary.md           # Shared glossary
│   ├── assets/               # Shared images, diagrams, stylesheets
│   └── common/               # IES Common module
│       ├── specification/    # Ontology files and spec docs
│       ├── user-guides/      # Conceptual guides and tutorials
│       ├── examples/         # Worked examples and sample data
│       ├── diagrams/         # Module-specific diagrams
│       ├── module.yml        # Module metadata
│       └── CHANGELOG.md      # Module version history
├── registry.yml              # Machine-readable module index
├── RELEASES.md               # Composite release documentation
└── [standard repo files]     # LICENSE, CONTRIBUTING, etc.
```

Future domain modules will be added under `docs/` following the same pattern:
- `docs/environment/building/` — IES Building module
- `docs/sdnp/{module}/` — SDNP domain modules

---

## Published Modules

| Module | Version | Status | Documentation |
|--------|---------|--------|---------------|
| **IES Common** | 5.1.0-rc2 | Release Candidate | [docs/common/](docs/common/) |

---

## Versioning

Each module is versioned independently using [Semantic Versioning](https://semver.org/):

- **MAJOR** — Incompatible changes (removing terms, changing IRIs)
- **MINOR** — Backwards-compatible additions (new terms, properties)
- **PATCH** — Backwards-compatible fixes (labels, annotations, documentation)

### Git Tags

- **Module releases:** `{module-id}/v{version}` (e.g., `common/v5.0.0`)
- **Release candidates:** `{module-id}/v{version}-rcN` (e.g., `common/v5.1.0-rc2`)
- **Composite releases:** `ies-release-{yyyy.mm}` (e.g., `ies-release-2025.06`)

---

## Governance and Custodianship  

While the Information Exchange Standard is not a legal entity, it represents a collaborative effort across multiple UK government bodies, including (but not limited to):

- Department for Business and Trade (DBT) *(custodian of this repository)*  
- Defence Science and Technology Laboratory (Dstl)  
- Ministry of Defence (MOD)  
- Metropolitan Police  
- Foreign, Commonwealth & Development Office (FCDO)  
- Home Office (HO)  
- HM Revenue & Customs (HMRC)  

These organisations act as the custodians and decision-makers for the ongoing development of the Standard.  

The development of this work is supported by private sector suppliers and technical specialists engaged through formal agreements. Their contributions are formally recognised in the [`ACKNOWLEDGEMENTS.md`](./ACKNOWLEDGEMENTS.md) file.  

---  

## Quick Links

- **Documentation:** [docs/index.md](docs/index.md)
- **IES Common Specification:** [docs/common/specification/](docs/common/specification/)
- **User Guides:** [docs/common/user-guides/](docs/common/user-guides/)
- **Examples:** [docs/common/examples/](docs/common/examples/)
- **Module Registry:** [registry.yml](registry.yml)
- **IES Website:** [informationexchangestandard.org](https://www.informationexchangestandard.org)

---  

## Project History  

This repository replaces the earlier [`IES4`](https://github.com/dstl/IES4) repository, originally hosted by the Defence Science and Technology Laboratory (Dstl), which was archived on 4 March 2025.  

Following that archive, the work was migrated here, adapted, and extended to support ongoing collaboration, development, and publication of new domain-specific extensions. This repository is now the authoritative and actively maintained home of the Information Exchange Standard.  

---  

## Licensing  

This repository contains both source code and documentation, each released under separate terms:  

- **Code** – Licensed under the [MIT License](./LICENSE.md)  
- **Documentation** – Licensed under the [Open Government Licence v3.0 (OGL-UK-3.0)](./OGL_LICENSE.md)  

By contributing to this repository, you agree that your contributions will be licensed under these terms.  

© Crown copyright (2020–2026)  

---  

## Contributions and Feedback  

We welcome:  
- Feedback and structured suggestions  
- Bug reports and clarifications  
- Requests for extensions or additional documentation  

Please see:  
- [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution guidelines  
- [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) for expected behaviour and reporting concerns  
- [MAINTAINERS.md](./MAINTAINERS.md) for maintainer contact information  

---
