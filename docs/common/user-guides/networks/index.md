# Network Concepts

This section provides guidance on modelling interconnected systems using the IES Common ontology. Whether you're working with road networks, utility infrastructure, supply chains, or any other domain involving connected elements and flows, these guides will help you understand and apply the relevant IES patterns.

These guides cover the core concepts of networks, connections, flows, and containment, providing practical examples and best practices for implementation and complement the [examples](../../examples/).

---

## Overview

The network concepts in IES provide a comprehensive framework for modelling:

- **Networks** - collections of interconnected links and nodes
- **Connections** - relationships enabling flow between elements
- **Flows** - matter, energy, or signal passing through networks
- **Containment** - the containment is the sum of the contained and its container

These concepts work together to support domains such as transport infrastructure, utility networks, logistics, and process engineering.

---

## Guides in This Section

### [Network](network.md)

The foundational guide for understanding how IES models networks of links and nodes. Covers networks that change over time, multiple levels of detail, connections between networks, and the relationship with EU INSPIRE network models.

**Key concepts:** Link, Node, Network, routing, graph extraction

---

### [Connection](connection.md)

Detailed guidance on representing connections between elements where flows can occur. Includes engineering examples (USB connections, bolted flanges, welded joints) and map-based connections (road polygons, road links).

**Key concepts:** Connection, Connector, ConnectionSide, connection types

---

### [Flow](flow.md)

How to model flows of matter, energy, or signal that cross surfaces or pass along paths. Covers traffic flows, fluid flows, energy flows, and how flows participate in events.

**Key concepts:** Flow, boundaries, flow relationships, containment of flows

---

### [Containment](containment.md)

Modelling containment relationships where one element contains others. Covers containers, contained elements, and how containment states change over time.

**Key concepts:** Containment, Container, Contained, nested containment

---

### [Location and Containment](location-and-containment.md)

A technical discussion comparing the existing `inLocation` relationship with the containment extension, explaining when to use each approach and how they differ semantically.

**Key concepts:** inLocation vs Containment, interior spaces, semantic distinctions

---

## Recommended Reading Order

For those new to the network concepts, we recommend the following order:

1. **[Network](network.md)** - Start with the foundational concepts of links, nodes, and networks
2. **[Connection](connection.md)** - Understand how elements are connected
3. **[Flow](flow.md)** - Learn how matter, energy, and signal move through networks
4. **[Containment](containment.md)** - Understand containment relationships
5. **[Location and Containment](location-and-containment.md)** - Explore the semantic distinctions

---

## Related Documentation

- [Introduction to IES](../introduction.md) - For background on IES fundamentals
- [4D Ontology Approach](../4d-ontology.md) - Understanding how time is modelled
- [Instantiation Patterns](../instantiation-patterns.md) - Standard patterns for creating IES data
- [Extending IES](../extending-ies.md) - How to extend these concepts for your domain

---

*These guides were developed from the original IES network extension documentation. For technical specifications, see the [IES Common Specification](../../specification/ies-common.md).*
