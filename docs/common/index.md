# IES Common

*Version: 5.0.0 (Release Candidate)*  
*Last Updated: 2026-01-25*  
*© Crown Copyright 2020-2026*

---

IES Common is the foundational ontology module of the Information Exchange Standard. It provides the core classes and properties for 4D extensional modelling of entities, states, and events, upon which all other IES modules are built.

---

## Overview

IES Common defines the fundamental concepts required for information exchange:

- **Elements** — Things with spatio-temporal extent (physical things)
- **Entities** — Tangible things with whole-life continuity (people, organisations, devices, locations)
- **States** — Temporal parts of entities during which properties hold
- **Events** — Activities or incidents involving participating entities
- **Periods of Time** — Temporal extents that can bound states and events
- **Representations** — Names, identifiers, and other ways of referring to things
- **Attributes** — Properties relating things to literal values

---

## Module Contents

### [Specification](specification/)

The complete technical specification of IES Common, including:

- Class hierarchy and definitions
- Property definitions with domains and ranges
- Ontology files in multiple serialisation formats (Turtle, RDF/XML, JSON-LD, N3)
- SHACL constraints

### [User Guides](user-guides/)

Conceptual guides for understanding and using IES Common:

- [Introduction to IES](user-guides/introduction.md) — Purpose and philosophy
- [What is an Ontology?](user-guides/what-is-an-ontology.md) — Foundational concepts
- [4D Ontology Approach](user-guides/4d-ontology.md) — Temporal modelling fundamentals
- [BORO Methodology](user-guides/boro-methodology.md) — Extent-based identity
- [Instantiation Patterns](user-guides/instantiation-patterns.md) — Creating IES-compliant data
- [Extending IES](user-guides/extending-ies.md) — Extension mechanisms

### [Examples](examples/)

Worked examples demonstrating IES Common patterns:

- Example scenarios with explanations
- Sample data files in Turtle format

### [Glossary](glossary.md)

Definitions of key terms used throughout IES Common documentation.

### [Changelog](CHANGELOG.md)

Version history and release notes for IES Common.

---

## Quick Reference

### Core Classes

| Class | Purpose |
|-------|--------|
| `ies:Thing` | Top-level class; everything in IES is a Thing |
| `ies:Element` | An individual thing with spatio-temporal extent |
| `ies:Entity` | A tangible thing with continuity through time |
| `ies:State` | A temporal part of an Entity |
| `ies:Event` | Something that happens, involving participation by Entities |
| `ies:PeriodOfTime` | A temporal extent that can bound States and Events |

### Core Properties

| Property | Purpose |
|----------|--------|
| `ies:isPartOf` | Mereological part-whole relationship |
| `ies:isStateOf` | Links a State to its parent Entity |
| `ies:isParticipantIn` | Links an Entity to an Event |
| `ies:inPeriod` | Associates an Element with a PeriodOfTime |

---

## Namespace

```
http://informationexchange.org/ont/ies/common/
```

Prefix: `ies:`

---

## Dependencies

IES Common has no dependencies on other IES modules. It is the foundation upon which all other modules build.

---

## Modules that Extend IES Common

- [IES Building](../environment/building/) — Buildings and structures (Environment domain)

*Additional modules will be listed as they are published.*

---

## Related Resources

- [IES Documentation Home](../index.md) — All IES modules
- [Module Registry](../../registry.yml) — Machine-readable module index
- [GitHub Repository](https://github.com/aigora-de/ont-ies) — Source and issue tracking

---

*© Crown Copyright 2020-2026 | Licensed under the MIT Licence*
