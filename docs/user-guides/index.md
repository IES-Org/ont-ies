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

## Audience-Specific Pathways

### For Implementers
Building systems that consume or produce IES data:

1. [Introduction to IES](introduction.md)
2. [4D Ontology Approach](4d-ontology.md) - focus on practical implications
3. [Instantiation Patterns](instantiation-patterns.md)
4. Review [Examples](../examples/index.md)

### For Information Architects
Designing information exchanges or mapping schemas:

1. [What is an Ontology?](what-is-an-ontology.md)
2. [Introduction to IES](introduction.md)
3. [4D Ontology Approach](4d-ontology.md)
4. [BORO Methodology](boro-methodology.md)
5. [Extending IES](extending-ies.md)

### For Data Modellers
Mapping existing schemas to/from IES:

1. [Introduction to IES](introduction.md)
2. [What is an Ontology?](what-is-an-ontology.md)
3. [Instantiation Patterns](instantiation-patterns.md)
4. [Extending IES](extending-ies.md)

### For Ontology Engineers
Working on IES itself or advanced extensions:

1. [BORO Methodology](boro-methodology.md)
2. [4D Ontology Approach](4d-ontology.md)
3. [Extending IES](extending-ies.md)
4. Review [Specification](../specification/index.md)

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

**Documentation Version:** 5.0.0  
**Last Updated:** November 2025  
**Applies to:** IES Common 4.x releases

---

*© Crown Copyright 2020-2025 | Licensed under the MIT Licence*