# Glossary

This glossary defines key terms used throughout the IES Common ontology documentation. Terms are organised alphabetically for easy reference.

---

## A

### Attribute
A datatype property in IES that relates a `Thing` to a literal value (string, number, date, etc.). Attributes are distinguished from relationships, which relate `Things` to other `Things`.

---

## B

### BORO (Business Objects Reference Ontology)
A methodology for developing ontologies based on extent-based identity criteria. BORO identifies things by their spatio-temporal extent rather than by names or descriptions. IES is guided by the BORO approach.

### Bounding State
A `State` that marks the beginning or end of another `State` or `Event`. For example, a birth is the bounding state that marks the start of a person's life.

---

## C

### Capacity
A `ClassOfState` representing what a `State` of an Entity *can* do in some possible world (modal possibility). A Capacity expresses potential rather than actuality—a State can have a Capacity without ever actualising it. For example, a State of "Fighter XYZ-123 in operational condition" can have the Capacity "Performer of Mach 2 flight" even if that aircraft has never actually flown at Mach 2. Having a Capacity (`hasCapacity`) is distinct from actualising it (`rdf:type`). See also [Capacity user guide](user-guides/capacity.md).

### Characteristic
A qualitative property of an `Element`. Unlike `Measures`, characteristics are not quantifiable on a numeric scale. Examples include colour, disposition, or accent.

### ClassOfElement
A class or category of `Elements`. ClassOfElement allows IES to model types and categories of things. For example, "Person" is a ClassOfElement whose members are all individual people.

### ClassOfEntity
A subclass of `ClassOfElement` specifically for categorising `Entities`. Used with the `ies:powertype` relationship to create type hierarchies.

### Connection
An `Element` that enables one or more `Flows` between two or more other `Elements`. A Flow can be of a fluid (such as water or natural gas), of energy (such as heat or electricity), of signal conveying information, of discrete entities (such as people, goods on pallets, or vehicles), or of mechanical load. See also [Connection user guide](user-guides/networks/connection.md).

### ConnectionSide
An `Element` that is a part of a `Connection` and part of an `Element` that is the source or destination of a flow through the Connection. A ConnectionSide can be all or part of a `Connector`.

### Connector
An `Element` that is, or is intended to, enable a `Connection` by being part of another `Element`. A Connector can exist without being part of another Element, and can be part of another Element without also being part of a Connection.

### Contained
An `Element` that is a part of a `Containment` and that is confined, protected, or handled. See also [Containment user guide](user-guides/networks/containment.md).

### Container
An `Element` that is, or is intended to, confine, protect or enable the handling of one or more `Contained` elements. A Container can exist without having a Contained element.

### Containment
An `Element` that confines, protects, or enables the handling of one or more `Contents`. See also [Containment user guide](user-guides/networks/containment.md).

### Continuous State
A `State` with a single, uninterrupted temporal extent. Contrasts with `DiscontinuousState`.

---

## D

### Discontinuous State
A `State` composed of multiple temporally separated periods. For example, "usually parked at home" represents a discontinuous state—the collection of all times a vehicle was parked at that location, without needing to identify each individual occurrence.

### Disposition
A `Characteristic` describing an `Element`'s capability or tendency to do something or exhibit a property, regardless of whether it has actually done so. For example, an aircraft capable of Mach 2 has that disposition even if it has never flown that fast.

---

## E

### eachHasCapacity
A relationship that asserts all members of a `ClassOfState` can have (be members of) a particular `ClassOfState` (Capacity). This is the class-level equivalent of `hasCapacity`. For example, "Every Eurofighter in operational condition can fly at Mach 2" uses `eachHasCapacity` to assert this capability at the class level, whereas `hasCapacity` would be used for a specific aircraft State. Domain: `ies:ClassOfState`. Range: `ies:ClassOfState`. See [Capacity](user-guides/capacity.md).

### Element
Anything with spatio-temporal extent—things that occupy space and time. The fundamental class in IES from which `Entity`, `State`, `Event`, and `PeriodOfTime` all descend. Informally: "things you can kick."

### Entity
A tangible thing with whole-life extent, such as a `Person`, `Device`, `Location`, or `Organisation`. Entities are modelled as their complete four-dimensional existence through time.

### Event
An activity or incident occurring at a specific point in time, involving one or more participating `Entities` through their `States`. Examples include meetings, telephone calls, arrests, or transactions. The extent of an Event is the sum of all its participants' extents.

### EventParticipant
A `State` of an `Entity` that participates in an `Event`. For example, "Fred attending the meeting" is an EventParticipant—it's a State of Fred that is part of the meeting Event.

### Exchanged Item
Anything that can be exchanged using IES. All IES classes descend from `Thing`, which is a subclass of `ExchangeItem`.

### Extensional Ontology
An ontology where identity is determined by extent rather than by intension (definition). Two things with the same extent are considered the same thing. IES is an extensional ontology.

### Extent
The "size" or "reach" of a thing. For physical things (`Elements`), extent is spatio-temporal—the space and time occupied. For classes, extent is the complete membership of the class.

---

## F

### Flow
A `State` that is the matter, energy or signal that crosses a surface or passes along a path. Flows can be connected together to form a `Network`. A Flow can also be called a 'stream'. See also [Flow user guide](user-guides/networks/flow.md).

### FlowAcrossSurface
A `Flow` that is across a surface. FlowAcrossSurface instances can serve as the start or finish boundaries of a `FlowAlongPath`.

### FlowAlongPath
A `Flow` that is along a path. A FlowAlongPath has start and finish boundaries that are `FlowAcrossSurface` instances.

### FlowNode
A `State` and a `Node` that is at the end of one or more `Flows`. Flows can merge or divide at a FlowNode.

### Four-Dimensional (4D) Ontology
An ontological approach that treats time the same way as space. Things exist as four-dimensional objects with three spatial dimensions and one temporal dimension. Changes to things are modelled as different temporal parts (States) of those things.

---

## H

### hasCapacity
A relationship that asserts a `State` can have (be a member of) a particular `ClassOfState` (Capacity). This expresses modal possibility: the State, in some possible world, can be a member of the specified ClassOfState. This is distinct from actually being a member (`rdf:type`). For example, "Sandown Hall during 2024 has the capacity to shelter displaced persons" means that State *can* be a member of the "Shelter displaced persons" ClassOfState, whether or not it ever actualises that capacity. Domain: `ies:State`. Range: `ies:ClassOfState`. See also [Capacity user guide](user-guides/capacity.md).

---

## I

### IDEAS (International Defence Enterprise Architecture Standard)
A 5EYES collaborative ontology (Australia, Canada, France, Sweden, UK, US, NATO) that influenced defence architecture frameworks including DoDAF, MODAF, NAF, and UPDM. IES extends and adapts IDEAS for broader UK Government use.

### Identifier
A `Representation` that uniquely identifies a `Thing` within a particular `NamingScheme`. Examples include national insurance numbers, passport numbers, MAC addresses, or database IDs.

### Identity Criteria
The rules for determining whether two things are the same or different. In BORO and IES, identity criteria are based on extent: things with the same spatio-temporal extent have the same identity.

### Instantiation
The process of creating instances (individual examples) of classes. IES supports multiple instantiation patterns for creating Elements, Names, and class instances.

### ISO15926
An international standard for lifecycle data sharing in the oil and gas industry, based on BORO methodology. Demonstrates the real-world applicability of extent-based ontologies.

---

## L

### Link
An `Element` that is, or enables, a `Flow` between the ends. A Link can be bi-directional, or uni-directional with a start end and a finish end. The ends of a Link can change during its life. Links connect `Nodes` in a `Network`. See also [Network user guide](user-guides/networks/network.md).

---

## M

### Measure
A `Characteristic` that is quantifiable on a numeric scale. Measures can be represented with different units (e.g., the same mass as "1kg" or "2.2lbs"). IES provides classes for SI base units.

### MeasureValue
A `Representation` of a `Measure`'s value, optionally with an associated `UnitOfMeasure`. The same Measure can have multiple MeasureValues in different units.

---

## N

### Name
A `Representation` that identifies or refers to a `Thing` within a specific linguistic or cultural context. Unlike `Identifiers`, names are not necessarily unique—many people can share the same name.

### Naming Scheme
A classification system for `Names` and `Identifiers`, often associated with a particular `Organisation` or `System`. For example, "National Insurance Number" is a naming scheme owned by the UK Department for Work and Pensions.

### Network
An `Element` that consists of `Links` and `Nodes`. A Network can consist of roads, railways, pipelines, `Flows` of energy or matter, or transport services conveying people or goods. A Network can change over time as Links or Nodes are added or removed. See also [Network user guide](user-guides/networks/network.md).

### Node
An `Element` that exists at the end of one or more `Links`. A Node is all or part of the `Connector` at the end of a Link, and can be a `Connection`. A Node can be at the end of different Links during its life. See also [Network user guide](user-guides/networks/network.md).

---

## O

### Ontology
A formal model of things we're interested in, defining physical things, types of things, and relationships between them. A proper ontology has underpinning in formal logic and/or set theory, consistent patterns for common concepts, and a repeatable methodology.

---

## P

### Parsimony
The principle of avoiding unnecessary proliferation of concepts. In IES development, parsimony means preferring to reuse existing patterns or extend existing concepts rather than creating new ones.

### PeriodOfTime
An `Element` representing a specific period of time (past, present, or future). Periods have a temporal extent but their spatial extent is considered to be everywhere of interest. Examples include "January 2024" or "10:00–11:00 on 15 March 2025."

### Powertype
A relationship between two classes where one class is the set of all possible subsets of the other (the powerset). Used in IES to "push up" type levels. For example, `ClassOfEntity` is a powertype of `Entity`.

---

## R

### RDF (Resource Description Framework)
A W3C standard for representing information as subject-predicate-object triples. IES is specified as an RDF Schema, enabling use of standard serialisations (Turtle, JSON-LD, RDF/XML) and extensive tool support.

### rdfs:subClassOf
The RDF Schema relationship indicating that one class is a subclass (more specific type) of another. For example, `Person` is a subclass of `Entity`.

### rdfs:subPropertyOf
The RDF Schema relationship indicating that one property is a sub-property (more specific relationship) of another.

### rdf:type
The RDF relationship indicating that an individual is an instance of a class. For example, `data:Fred rdf:type ies:Person` states that Fred is a Person.

### Relationship
An object property in IES that relates one `Thing` to another `Thing`. Distinguished from attributes, which relate Things to literal values. The top-level relationship property in IES is `ies:relationship`.

### Representation
Something that stands for or describes a `Thing`. Representations include `Names`, `Identifiers`, `WorksOfDocumentation`, and `MeasureValues`. IES distinguishes between things in the real world and representations of those things.

### representationValue
A datatype property that provides the literal value of a `Representation`. For example, a Name might have `representationValue "Fred Smith"` and an Identifier might have `representationValue "AB123456C"`.

### Responsible Actor
An `Entity` capable of being held responsible for actions. Includes `Persons` and `Organisations`. ResponsibleActors can own naming schemes, participate in events, and enter into relationships.

---

## S

### Spatio-Temporal Extent
The four-dimensional "volume" occupied by a physical thing—its extent through three dimensions of space and one dimension of time. In IES, identity is based on spatio-temporal extent: things with the same extent are the same thing.

### State
A temporal part of an `Entity`. States represent phases, periods, or moments in an Entity's existence. For example, "Fred on Monday" is a State of Fred, as is "Fred while employed at Acme Corp." States can be of any duration and may overlap.

---

## T

### Temporal Extent
The duration or "reach" of something through time. All `Elements` in IES have temporal extent. For `Entities`, temporal extent can be divided into `States`.

### Thing
The top-level class in IES (after `ExchangeItem`). Everything in IES is a `Thing`. Thing has six main subtypes: `Element`, `ClassOfElement`, `State`, `Entity`, `Event`, and `PeriodOfTime`.

---

## U

### Unit of Measure
A `ClassOfMeasureValue` used to quantify a `Measure` on a standard scale. IES provides classes for SI base units (metres, kilograms, seconds, amperes, kelvin, moles, candela) and supports custom units.

### Upper Ontology
A foundational ontology providing fundamental concepts and patterns that can be extended for specific domains. IES Common is an upper ontology based on IDEAS, which can be extended for particular use cases.

---

## W

### WorkOfDocumentation
A `Representation` that documents or describes a `Thing`. Can be a physical document (`IndividualDocument`) or an abstract work that may have multiple copies.

---

## Acronyms

| Acronym | Expansion | Definition |
|---------|-----------|------------|
| **BORO** | Business Objects Reference Ontology | Methodology for extent-based ontology development |
| **DoDAF** | Department of Defense Architecture Framework | US defence architecture framework influenced by IDEAS |
| **HMG** | His/Her Majesty's Government | The UK Government |
| **IDEAS** | International Defence Enterprise Architecture Standard | 5EYES collaborative ontology that influenced IES |
| **IES** | Information Exchange Standard | UK Government ontology for information exchange |
| **ISO** | International Organization for Standardization | International standards body |
| **JSON-LD** | JavaScript Object Notation for Linked Data | RDF serialisation format based on JSON |
| **MODAF** | Ministry of Defence Architecture Framework | UK defence architecture framework |
| **NAF** | NATO Architecture Framework | NATO architecture framework |
| **ODM** | Ontology Definition Metamodel | OMG profile for UML-based ontology modelling |
| **OMG** | Object Management Group | International standards consortium |
| **OWL** | Web Ontology Language | W3C standard for expressing ontologies |
| **RDF** | Resource Description Framework | W3C standard for representing information |
| **RDFS** | RDF Schema | W3C vocabulary for describing RDF resources |
| **SI** | Système International (d'unités) | International System of Units |
| **SPARQL** | SPARQL Protocol and RDF Query Language | W3C standard query language for RDF |
| **UPDM** | Unified Profile for DoDAF and MODAF | OMG standard based on IDEAS |
| **URI** | Uniform Resource Identifier | Standard identifier format used in RDF |
| **W3C** | World Wide Web Consortium | International web standards organisation |
| **XML** | eXtensible Markup Language | W3C standard for data serialisation |

---

## Related Resources

For more detailed explanations of these concepts, see:

- [Introduction to IES](user-guides/introduction.md) - Overview of IES purpose and philosophy
- [What is an Ontology?](user-guides/what-is-an-ontology.md) - Fundamental ontology concepts
- [4D Ontology Approach](user-guides/4d-ontology.md) - Understanding the four-dimensional approach
- [BORO Methodology](user-guides/boro-methodology.md) - The BORO method and extent-based identity
- [Capacity](user-guides/capacity.md) - Guide to the Capacity pattern
- [Networks Overview](user-guides/networks/index.md) - Guide to network-related concepts
- [IES Specification](specification/) - Complete technical specification

---

*© Crown Copyright 2020-2026*
