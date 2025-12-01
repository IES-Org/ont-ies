---
title: IES Specification
description: Detailed specification of the Information Exchange Standard Common Ontology
---

*Version: 5.0.0*  
*Last Updated: 2025-11-29*  
*© Crown Copyright 2020-2025*

# IES Specification

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

The authoritative machine-readable definition of IES is maintained in:
- A UML model using the ODM RDF profile
- **ies-common.ttl** - RDF/Turtle ontology file

All documentation is derived from this source of truth.

---

## Overview

The Information Exchange Standard (IES) is a 4D extensional ontology designed to facilitate enterprise-level information exchange between producers and consumers in a precise way. IES is expressed as an RDF Schema with some OWL constructs.

### Core Philosophy

**Purpose**: To make information exchange easier by providing a common vocabulary for data/information exchanges between knowledge stores.

**4D Approach**: IES treats time the same way as space, allowing changes to entities to be described as temporal states.

**Identity Criteria**: Two things sharing the same 4D spatio-temporal extent are considered the same thing (same identity).

### Key Concepts

The IES is built on six fundamental subtypes of `Thing`:

- **Element**: Anything physical with extent in space and time
- **Entity**: Tangible things like people, devices, locations
- **ClassOfElement**: Classes or categories of elements  
- **State**: Temporal states of entities
- **Event**: Activities or incidents occurring at specific points in time
- **PeriodOfTime**: Specific periods of time (past, present, or future)
- **relationship**: Relates things together

### Design Principles

**Inclusion Criteria**: For information to be included in IES, three conditions must be met:
1. At least one organisation wants to share the information
2. At least one organisation wants to receive it
3. Someone is able and willing to define it

**Extensibility**: IES includes agile extension mechanisms allowing users to exchange information beyond any specific version without necessitating time-consuming standard revisions.

**Minimal Constraints**: IES is intentionally loosely constrained:
- Domains and ranges for properties are indicative, not restrictive
- Event participations don't formally constrain which entities can participate
- Goal: Allow any sending party to express information
- Expectation: IES will become more constrained over time in response to use cases

**Parsimony**: Ontology developers are parsimonious with new concepts, preferring to reuse extant patterns or extend from extant concepts.

---

## Legal disclaimer for "entity" and "event"

Some of the users of IES may be subject to the Investigatory Powers Act 2016 ("IPA"). This section of the standard is intended to clarify some terms that are used in IES that should not be confused or conflated with terminology from the
IPA.

For the purposes of the IES, the entity and event types that are supported within the standard are defined in the model. The meanings assigned to these terms operate solely and exclusively for the purposes of the IES in order to provide a standardised way of describing information to facilitate information sharing between organisations. Neither the IES, nor the categorisation of data pursuant to the IES, are otherwise relevant to each organisation's internal arrangements for categorising, handling or safeguarding data they hold.

The terms entities and events are separately defined in the UK for the purposes of the Investigatory Powers Act 2016 ("IPA"). The IPA definitions are limited to the telecommunications context and are therefore a subset of the entity and event types that are supported within the IES. Any data obtained or retained by an organisation under the IPA must be categorised according to the IPA definitions, and the IPA safeguards must be applied in accordance with those definitions.

---

## Related Documentation

- [User Guides](../user-guides/index.md) - Introduction to using IES
- [4D Ontology Introduction](../user-guides/4d-ontology.md) - Understanding the 4D approach
- [Instantiation Patterns](../user-guides/instantiation-patterns.md) - How to create IES instances
- [Extending IES](../user-guides/extending-ies.md) - How to extend IES for specific needs

---

*© Crown Copyright 2020-2025*