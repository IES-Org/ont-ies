# Welcome to the IES Common Ontology

The **Information Exchange Standard (IES) Common** is a standardised ontology for enterprise-level information exchange. This documentation provides comprehensive guidance for understanding, implementing, and extending IES.

---

## About IES

The IES was developed to enable collaboration across UK Government by providing a common vocabulary for data and information exchange between knowledge stores. Rather than creating numerous bespoke bilateral interfaces, organisations can convert information to and from the IES common format, dramatically reducing complexity and maintenance costs.

### Key Features

**4D Extensional Ontology** – IES treats time the same way as space, modelling changes to entities as temporal states with consistent spatio-temporal identity criteria.

**Minimally Constrained** – Domains and ranges for properties are indicative rather than restrictive, allowing flexibility whilst providing a useful framework for information exchange.

**Agile Extension Mechanisms** – Users can extend IES without necessitating time-consuming standard revisions, supporting information exchange beyond any specific version.

**RDF-Based** – Built on W3C RDF standards, providing multiple serialisation formats (Turtle, JSON-LD, RDF/XML) and extensive tool support.

---

## Documentation Structure

<div class="ies-doc-nav">
<a href="user-guides/" class="ies-doc-nav-card">
<h3>📚 User Guides</h3>
<p>Comprehensive guides covering IES fundamentals, the 4D ontology approach, instantiation patterns, extension mechanisms, and the BORO methodology.</p>
</a>

<a href="specification/" class="ies-doc-nav-card">
<h3>📋 Specification</h3>
<p>Complete technical specification including class hierarchies, property definitions, UML diagrams, and the authoritative ies-common.ttl ontology file.</p>
</a>

<a href="examples/" class="ies-doc-nav-card">
<h3>💡 Examples</h3>
<p>Practical worked examples demonstrating IES patterns in action, showing how to model real-world scenarios using the ontology.</p>
</a>

<a href="faq/" class="ies-doc-nav-card">
<h3>❓ FAQ</h3>
<p>Answers to frequently asked questions about IES concepts, implementation, extension, and usage patterns.</p>
</a>

<a href="glossary/" class="ies-doc-nav-card">
<h3>📖 Glossary</h3>
<p>Definitions of key terms, concepts, and technical vocabulary used throughout the IES ontology and documentation.</p>
</a>
</div>

---

## Quick Start Paths

### For Implementers
Start with the [Introduction to IES](user-guides/introduction.md) to understand the purpose and philosophy, then explore [Instantiation Patterns](user-guides/instantiation-patterns.md) to learn how to create IES-compliant data.

### For Information Architects
Begin with [What is an Ontology?](user-guides/what-is-an-ontology.md) and [The 4D Ontology Approach](user-guides/4d-ontology.md) to understand the theoretical foundations, then review the [Specification](specification/) for detailed class and property definitions.

### For Extenders
Review [Extending IES](user-guides/extending-ies.md) to understand extension mechanisms and best practices, then examine the [Examples](examples/) for practical patterns.

---

## Background

Across UK Government there are many separate knowledge stores, including multiple stores within each organisation. Many contain similar information about the real world but use different terminologies, formats and schemas. This creates significant challenges:

* Analysts need comprehensive access to information distributed across these stores without having to broker between different formats
* Organisations need to exchange information without developing numerous bespoke bilateral interchange mechanisms
* Systems need to integrate without costly and disruptive changes to individual knowledge stores

The IES addresses these challenges by providing a common vocabulary. Information from each store is converted to and from the common vocabulary when it travels, so users and systems only need to understand the relationship between their internal model and IES.

---

## Scope and Inclusion Criteria

The selection of information types included in IES is orientated towards those of greatest interest to working-level analysts across HMG. IES recognises that modelling the entire world would be unrealistic, and highly specialised information types are covered by specialist communities.

**Three criteria** must be met for including an information type in IES:

1. At least one organisation wants to share the information
2. At least one organisation wants to receive it
3. Someone is able and willing to define it

Users can exchange information beyond the scope of any specific version through IES's agile extension mechanisms.

---

## Design Philosophy

### Minimal Constraints

The IES model is intentionally loosely constrained. Domains and ranges for relationships (RDF properties) are purely indicative, not restrictive. Similarly, Event Participations don't formally constrain which Entities can participate in particular Events—rather, they indicate which should be used.

**The goal** is to allow any sending party to express the information they want whilst still providing a framework. Receiving parties should expect to receive such data.

**The expectation** is that the model will become more constrained over time as users provide feedback and IES adapts to different usage patterns.

### Parsimony

Ontology developers are parsimonious with new concepts, preferring to reuse existing patterns or extend from existing concepts rather than introducing unnecessary new elements.

### Extensibility

IES uses W3C RDF Schema, allowing new classes and properties to be defined in data payloads. When extending IES, users should subtype from the most appropriate class and specialise properties from existing properties. This aids understanding by receiving parties, which are likely to only know about the core IES classes.

---

## Implementation

From version 4.0.0, IES is specified as an RDF Schema. RDF is a standard published by the W3C and is the preferred data exchange format in UK Government.

**Major benefits of using RDF:**

* W3C has specified numerous standard data serialisations (Turtle, JSON-LD, RDF/XML, N-Triples)
* Wide implementation in commercial and open-source tools
* IES no longer needs to specify its own serialisations
* Any IES-compliant interface can read any W3C RDF standard serialisation format

The extensive ecosystem of open-source RDF software means this should not be a barrier to entry.

---

## A Note on Naming

The Information Exchange Standard, as its name suggests, was originally devised as a specification for exchange of data and information amongst organisations that need to collaborate. This purpose gave rise to the name of the standard.

However, this does not preclude IES from being used for wider purposes beyond data exchange. In fact, IES has already been used as a specification for data persistence in several organisational deployments.

Whilst changing the name to reflect wider applicability has been considered, it has been decided that for the time being—as the standard continues to mature and be promoted—a name change would not be helpful. This decision may be revisited in the future.

!!! warning "Important"
    Whilst IES may be used as a specification for data persistence, the standard itself does not provide any end-point implementation of such.

---

## Version Information

**Current Version:** 4.4.0  
**Licence:** MIT Licence (Crown Copyright 2020-2025)  
**Publisher:** UK Department for Business and Trade  
**Language:** British English (en-GB)

---

## Getting Started

Ready to begin? Here are some recommended starting points:

1. Read the [Introduction to IES](user-guides/introduction.md) for a comprehensive overview
2. Understand the [4D Ontology Approach](user-guides/4d-ontology.md) that underpins IES
3. Learn [What is an Ontology?](user-guides/what-is-an-ontology.md) if you're new to ontological modelling
4. Explore the [Specification](specification/) for detailed technical information
5. Study [Instantiation Patterns](user-guides/instantiation-patterns.md) to learn how to create IES data
6. Review [Examples](examples/) to see IES in practice

---

## Support and Feedback

IES is an evolving standard that responds to user feedback and real-world usage patterns. If you have questions, suggestions, or encounter issues, please consult the [FAQ](faq/) section.

---

*© Crown Copyright 2020-2025 | Licensed under the MIT Licence*