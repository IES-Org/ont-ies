---
title: IES Common Specification
description: Detailed specification of the Information Exchange Standard Common Ontology
---

*Version: 5.0.0*  
*Last Updated: 2025-11-29*  
*© Crown Copyright 2020-2025*

# IES Common Specification

This section contains the complete specification of the Information Exchange Standard (IES) Common ontology, including all class and property definitions, diagrams, and explanatory material.

## IES Model Diagrams

The [IES Model Diagrams](ies.md) document provides comprehensive visual documentation including:

- **Introduction Diagrams**: Notation, overview
- **Entity Diagrams**: People, organisations, locations, devices, accounts
- **Structural Diagrams**: Relationships, temporal modelling, event patterns
- **Event Diagrams**: Business events, communication, lifecycle, criminal activity
- **Relationship Diagrams**: Familial, professional, social, structural

---

## Authoritative Source

The authoritative machine-readable definition of IES Common is maintained in:

| Format | File | Description |
|--------|------|-------------|
| RDF/Turtle | [ies-common.ttl](ies-common.ttl) | Primary ontology definition |
| RDF/XML | [ies-common.rdf](ies-common.rdf) | XML serialisation |
| JSON-LD | [ies-common.json](ies-common.json) | JSON-LD serialisation |
| Notation3 | [ies-common.n3](ies-common.n3) | N3 serialisation |
| SHACL | [ies-common.shacl](ies-common.shacl) | Shape constraints |

All documentation is derived from the source UML model using the ODM RDF profile.

---

## Overview

The Information Exchange Standard (IES) Common is a 4D extensional ontology designed to facilitate enterprise-level information exchange between producers and consumers in a precise way. IES is expressed as an RDF Schema with some OWL constructs.

### Core Philosophy

**Purpose**: To make information exchange easier by providing a common vocabulary for data/information exchanges between knowledge stores.

**4D Approach**: IES treats time the same way as space, allowing changes to entities to be described as temporal states.

**Identity Criteria**: Two things sharing the same 4D spatio-temporal extent are considered the same thing (same identity).

### Key Concepts

The IES Common ontology is built on six fundamental subtypes of `Thing`:

- **Element**: Anything physical with extent in space and time
- **Entity**: Tangible things like people, devices, locations
- **ClassOfElement**: Classes or categories of elements  
- **State**: Temporal states of entities
- **Event**: Activities or incidents occurring at specific points in time
- **PeriodOfTime**: Specific periods of time (past, present, or future)

### Design Principles

**Inclusion Criteria**: For information to be included in IES, three conditions must be met:
1. At least one organisation wants to share the information
2. At least one organisation wants to receive it
3. Someone is able and willing to define it

**Extensibility**: IES includes agile extension mechanisms allowing users to exchange information beyond any specific version.

**Minimal Constraints**: IES is intentionally loosely constrained:
- Domains and ranges for properties are indicative, not restrictive
- Event participations don't formally constrain which entities can participate
- Goal: Allow any sending party to express information

**Parsimony**: Ontology developers are parsimonious with new concepts, preferring to reuse extant patterns or extend from extant concepts.

---

## Legal Disclaimer

Some users of IES may be subject to the Investigatory Powers Act 2016 ("IPA"). The entity and event types defined in IES operate solely for the purposes of the IES standard and should not be conflated with IPA terminology. The IPA definitions are limited to the telecommunications context and are a subset of the entity and event types supported within IES.

---

## Related Documentation

- [User Guides](../user-guides/index.md) - Introduction to using IES
- [4D Ontology Introduction](../user-guides/4d-ontology.md) - Understanding the 4D approach
- [Instantiation Patterns](../user-guides/instantiation-patterns.md) - How to create IES instances
- [Extending IES](../user-guides/extending-ies.md) - How to extend IES for specific needs
- [Examples](../examples/index.md) - Worked examples and sample data

---

*© Crown Copyright 2020-2025*
