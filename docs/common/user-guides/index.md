# User Guides

Welcome to the IES Common User Guides. This section provides comprehensive guidance for understanding, implementing, and extending the Information Exchange Standard (IES).

---

## About These Guides

The User Guides are designed to take you from foundational concepts through to advanced implementation patterns. Whether you're new to ontologies or an experienced information architect, you'll find the information you need to work effectively with IES.

---

## Getting Started

If you're new to IES, we recommend following this learning path:

<div class="ies-learning-path">

### 1. Foundational Understanding
Start with the basics to build a solid foundation:

- **[Introduction to IES](introduction.md)** - Understand what IES is, why it exists, and who should use it
- **[What is an Ontology?](what-is-an-ontology.md)** - Learn the fundamentals of ontological modelling

### 2. Core Concepts
Grasp the key concepts that underpin IES:

- **[4D Ontology Approach](4d-ontology.md)** - Understand how IES treats time as the fourth dimension
- **[BORO Methodology](boro-methodology.md)** - Learn about the Business Objects Reference Ontology principles

### 3. Practical Application
Put your knowledge into practice:

- **[Instantiation Patterns](instantiation-patterns.md)** - Learn standard patterns for creating IES data
- **[Extending IES](extending-ies.md)** - Discover how to extend IES for your specific needs

### 4. Network Concepts
Learn how to model interconnected systems:

- **[Network Concepts](networks/network.md)** - Understand how to model networks of links and nodes
- **[Connections](networks/connection.md)** - Learn how to represent connections between elements
- **[Flows](networks/flow.md)** - Model matter, energy, or signal passing through networks
- **[Containment](networks/containment.md)** - Represent containment relationships between elements

</div>

---

## User Guide Index

### [Introduction to IES](introduction.md)
A comprehensive introduction to the Information Exchange Standard, covering its purpose, key features, design philosophy, and core concepts. Essential reading for anyone new to IES.

**Topics covered:**

- Purpose and benefits of IES
- The problem IES solves
- Design philosophy and principles
- Core ontology concepts
- Worked examples

---

### [What is an Ontology?](what-is-an-ontology.md)
An accessible introduction to ontologies for those new to the concept, explaining what ontologies are, how they differ from other data models, and why they're useful for information exchange.

**Topics covered:**

- Definition and purpose of ontologies
- Ontologies vs. databases
- Ontologies vs. taxonomies
- RDF and semantic web basics
- Benefits for information sharing

---

### [4D Ontology Approach](4d-ontology.md)
Detailed explanation of the 4D extensional ontology approach that underpins IES, where time is treated as the fourth dimension alongside the three spatial dimensions.

**Topics covered:**

- Spatio-temporal extent and identity
- States vs. Entities
- Temporal parts
- The 4D vs. 3D modelling debate
- Practical implications for data modelling

---

### [BORO Methodology](boro-methodology.md)
Introduction to the Business Objects Reference Ontology (BORO) methodology, which provides the theoretical and practical foundations for IES.

**Topics covered:**

- BORO principles
- Extensional identity
- Powerset patterns
- Consistency with 4D ontology
- Application to enterprise modelling

---

### [Instantiation Patterns](instantiation-patterns.md)
Comprehensive guide to standard patterns for creating IES-compliant instance data, with practical examples and best practices.

**Topics covered:**

- Entity and State patterns
- Event participation patterns
- Temporal extent patterns
- Identifier patterns
- Representation patterns
- Relationship patterns

---

### [Extending IES](extending-ies.md)
Guidance on how to extend IES for domain-specific or organisation-specific needs whilst maintaining interoperability and semantic consistency.

**Topics covered:**

- Extension principles
- Finding the right extension point
- Creating subclasses and subproperties
- Powertype patterns for extensions
- Dual typing for backward compatibility
- Best practices and common pitfalls

---

### Network Concepts

The network documentation provides guidance on modelling interconnected systems such as road networks, utility networks, and other infrastructure.

#### [Network](networks/network.md)
Comprehensive guide to modelling networks consisting of links and nodes, including how networks change over time and how to handle multiple levels of detail.

**Topics covered:**

- Links and Nodes fundamentals
- Networks that change with time
- Levels of detail in network modelling
- Connections between networks
- Routing and graph extraction
- Mapping between IES and INSPIRE network models

---

#### [Connection](networks/connection.md)
Detailed guidance on representing connections between elements where flows can occur, including engineering connections and map-based connections.

**Topics covered:**

- Connection types (overlap, common boundary, intermediate elements)
- Connectors and ConnectionSides
- Engineering connection examples (USB, bolted flange, welded)
- Connections as nodes in networks
- Road network connections and polygons

---

#### [Flow](networks/flow.md)
Guide to modelling flows of matter, energy, or signal that cross surfaces or pass along paths, including traffic flows, fluid flows, and energy flows.

**Topics covered:**

- Flow fundamentals and the Eulerian view
- Connections between flows (merge, divide, join)
- Flow participation in events
- Containment of flows
- Traffic monitoring and flow measurement

---

#### [Containment](networks/containment.md)
Guide to modelling containment relationships where one element contains others, including containers, contained elements, and containment states.

**Topics covered:**

- Container and Contained relationships
- Containment as an Element (not State)
- Nested containment examples
- Containment properties over time

---

#### [Location and Containment](networks/location-and-containment.md)
Discussion of the relationship between the existing `inLocation` relationship and the containment extension, showing how the two approaches are consistent but containment adds additional semantics.

**Topics covered:**

- Comparison of inLocation and Containment approaches
- Batch of fluid in tank examples
- Interior space identification
- When to use location vs. containment

---

## Audience-Specific Pathways

### For Implementers
Building systems that consume or produce IES data:

1. [Introduction to IES](introduction.md)
2. [4D Ontology Approach](4d-ontology.md) - focus on practical implications
3. [Instantiation Patterns](instantiation-patterns.md)
4. [Network Concepts](networks/network.md) - if working with network data
5. Review [Examples](../examples/index.md)

### For Information Architects
Designing information exchanges or mapping schemas:

1. [What is an Ontology?](what-is-an-ontology.md)
2. [Introduction to IES](introduction.md)
3. [4D Ontology Approach](4d-ontology.md)
4. [BORO Methodology](boro-methodology.md)
5. [Network Concepts](networks/network.md) - for infrastructure domains
6. [Extending IES](extending-ies.md)

### For Data Modellers
Mapping existing schemas to/from IES:

1. [Introduction to IES](introduction.md)
2. [What is an Ontology?](what-is-an-ontology.md)
3. [Instantiation Patterns](instantiation-patterns.md)
4. [Connection](networks/connection.md) - for relationship mapping
5. [Extending IES](extending-ies.md)

### For Ontology Engineers
Working on IES itself or advanced extensions:

1. [BORO Methodology](boro-methodology.md)
2. [4D Ontology Approach](4d-ontology.md)
3. [Network Concepts](networks/network.md) - understanding the network extension
4. [Location and Containment](networks/location-and-containment.md) - semantic distinctions
5. [Extending IES](extending-ies.md)
6. Review [Specification](../specification/index.md)

### For Infrastructure Domain Specialists
Working with road, rail, utility, or other network-based domains:

1. [Introduction to IES](introduction.md)
2. [4D Ontology Approach](4d-ontology.md)
3. [Network Concepts](networks/network.md)
4. [Connection](networks/connection.md)
5. [Flow](networks/flow.md)
6. [Containment](networks/containment.md)

---

## Additional Resources

### Related Documentation

- [Specification](../specification/index.md) - Complete technical specification
- [Examples](../examples/index.md) - Worked examples and sample data
- [Glossary](../glossary.md) - Terminology and definitions

---

## Document Conventions

Throughout these guides, you'll encounter:

!!! note "Informational Notes"
    Additional context or clarifications

!!! tip "Best Practices"
    Recommended approaches and tips

!!! warning "Important Considerations"
    Critical information to be aware of

!!! example "Worked Examples"
    Practical demonstrations with code

**Code Examples:**
```turtle
# RDF/Turtle examples use this style
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .

data:example_1 a ies:Person .
```

**Technical Terms:**
Key terms are emphasised and defined in the [Glossary](../glossary.md).

---

## Providing Feedback

IES is an evolving standard that improves through user feedback. If you:

- Find errors or unclear explanations
- Have suggestions for improvements
- Encounter use cases not covered
- Want to contribute examples

Please [open an issue](https://github.com/IES-Org/ies-common/issues) on our GitHub repository or contact the IES team.

---

## Version Information

**Documentation Version:** 5.1.0  
**Last Updated:** 06 January 2026  
**Applies to:** IES Common 5.x releases

---

*© Crown Copyright 2020-2026 | Licensed under the MIT Licence*
