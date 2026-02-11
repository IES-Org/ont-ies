# Welcome to the IES Ontology Documentation

The **Information Exchange Standard (IES)** is a standardised ontology suite for enterprise-level information exchange. This documentation provides comprehensive guidance for understanding, implementing, and extending IES modules.

---

## About IES

The IES was developed to enable collaboration across UK Government by providing a common vocabulary for data and information exchange between knowledge stores. Rather than creating numerous bespoke bilateral interfaces, organisations can convert information to and from the IES common format, dramatically reducing complexity and maintenance costs.

### Key Features

**4D Extensional Ontology** – IES treats time the same way as space, modelling changes to entities as temporal states with consistent spatio-temporal identity criteria.

**Minimally Constrained** – Domains and ranges for properties are indicative rather than restrictive, allowing flexibility whilst providing a useful framework for information exchange.

**Modular Architecture** – IES consists of a foundational module (IES Common) and domain-specific extensions, allowing organisations to adopt only what they need.

**Agile Extension Mechanisms** – Users can extend IES without necessitating time-consuming standard revisions.

**RDF-Based** – Built on W3C RDF standards, providing multiple serialisation formats and extensive tool support.

---

## IES Modules

IES is organised into modules, each serving a specific purpose:

### Foundation

<div class="ies-doc-nav">

<a href="common/specification/" class="ies-doc-nav-card">
<h3>📘 IES Common</h3>
<p>The foundational ontology providing core classes and properties for 4D extensional modelling of entities, states, and events. Required by all other modules.</p>
<p><strong>Latest:</strong> v5.0.0 (Release Candidate)</p>
</a>

</div>

### Environment Domain

<div class="ies-doc-nav">

<a href="environment/building/specification/" class="ies-doc-nav-card">
<h3>🏢 IES Building</h3>
<p>Ontology module for describing buildings, structures, and their spatial and functional characteristics within the built environment.</p>
<p><strong>Latest:</strong> v0.1.0 (Development)</p>
<p><em>Depends on: IES Common ≥ 5.0.0</em></p>
</a>

</div>

*Additional domain modules (SDNP) will be added as they are published.*

---

## Documentation Structure

### Module Documentation

Each module contains:

- **specification/** – Ontology files and technical specification
- **user-guides/** – Conceptual guides and tutorials
- **examples/** – Worked examples and sample data
- **CHANGELOG.md** – Version history
- **module.yml** – Machine-readable metadata

### Shared Resources

- **[Glossary](glossary.md)** – Definitions of key terms across all modules
- **[Assets](assets/)** – Shared images, diagrams, and stylesheets

---

## Quick Start

### For Implementers
Start with the [Introduction to IES](common/user-guides/introduction.md) to understand the purpose and philosophy, then explore [Instantiation Patterns](common/user-guides/instantiation-patterns.md) to learn how to create IES-compliant data.

### For Information Architects
Begin with [What is an Ontology?](common/user-guides/what-is-an-ontology.md) and [The 4D Ontology Approach](common/user-guides/4d-ontology.md) to understand the theoretical foundations, then review the [Specification](common/specification/) for detailed class and property definitions.

### For Extenders
Review [Extending IES](common/user-guides/extending-ies.md) to understand extension mechanisms and best practices, then examine the [Examples](common/examples/) for practical patterns.

---

## Registry

The [Module Registry](../registry.yml) provides a machine-readable index of all published IES modules, their versions, and compatibility information.

---

## Module Status

| Module | Domain | Version | Status |
|--------|--------|---------|--------|
| [IES Common](common/specification/) | Foundation | 5.0.0 | Release Candidate |
| [IES Building](environment/building/specification/) | Environment | 0.1.0 | Development |

**Licence:** MIT Licence (Crown Copyright 2020-2026)  
**Publisher:** UK Department for Business and Trade  
**Language:** British English (en-GB)

---

## Getting Started with IES Common

Ready to begin? Here are recommended starting points:

1. Read the [Introduction to IES](common/user-guides/introduction.md) for a comprehensive overview
2. Understand the [4D Ontology Approach](common/user-guides/4d-ontology.md) that underpins IES
3. Learn [What is an Ontology?](common/user-guides/what-is-an-ontology.md) if you're new to ontological modelling
4. Explore the [Specification](common/specification/) for detailed technical information
5. Study [Instantiation Patterns](common/user-guides/instantiation-patterns.md) to learn how to create IES data
6. Review [Examples](common/examples/) to see IES in practice

---

## Support and Feedback

IES is an evolving standard that responds to user feedback and real-world usage patterns. If you have questions, suggestions, or encounter issues, please open an issue on the [GitHub repository](https://github.com/aigora-de/ont-ies).

---

*© Crown Copyright 2020-2026 | Licensed under the MIT Licence*
