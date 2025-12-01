# IES Sample Data

This section provides practical RDF/Turtle (`.ttl`) examples demonstrating how to use IES patterns for common scenarios. Each sample file is a complete, valid IES instance data set that you can load into an RDF triple store or use as a template for your own data.

---

## About These Examples

All sample files use the **Turtle** (Terse RDF Triple Language) serialisation format and demonstrate proper use of:

- IES classes and properties
- Standard prefixes and namespaces
- Instantiation patterns
- Temporal modelling with States
- Event participation
- Identifiers and names

---

## Available Samples

### Core Patterns

#### Assessment
**File:** `assessment.ttl`

Demonstrates the IES assessment pattern for modelling subjective judgements and confidence levels about possible scenarios.

**Key concepts:**
- `ies:PossibleWorld` - Alternative scenarios
- `ies:AssessToBeTrue` - Assessment events
- `ies:Assessor` - Analyst making assessments
- Confidence levels (HIGH, MEDIUM, LOW)

**Use cases:** Intelligence analysis, risk assessment, scenario planning

---

#### Characteristics and Measures
**File:** `characteristics-and-measures.ttl`

Shows how to model quantitative and qualitative properties of entities with different units of measure.

**Key concepts:**
- `ies:Mass` - Quantitative measurement
- `ies:Measure` - Base measurement class
- `ies:MeasureValue` - Values with units
- `ies:UnitOfMeasure` - Standard units (kilograms, pounds)

**Use cases:** Physical measurements, entity properties, scientific data

---

#### Event Participation
**File:** `event-participation.ttl`

Illustrates how entities participate in events through EventParticipant states.

**Key concepts:**
- `ies:Event` - Activities or incidents
- `ies:EventParticipant` - Participation states
- `ies:isParticipantIn` / `ies:isParticipationOf` - Participation relationships

**Use cases:** Meetings, transactions, activities involving multiple parties

---

#### Events
**File:** `events.ttl`

Basic event modelling showing temporal bounds and relationships.

**Key concepts:**
- `ies:Event` - Time-bounded activities
- `ies:BoundingState` - Start and end markers
- `ies:PeriodOfTime` - Temporal extents

**Use cases:** Scheduling, historical events, process tracking

---

#### Identifiers
**File:** `identifiers.ttl`

Demonstrates how to assign names and identifiers to entities using naming schemes.

**Key concepts:**
- `ies:Identifier` - Unique identifiers
- `ies:Name` - Human-readable names
- `ies:NamingScheme` - Classification of identifiers
- `ies:representationValue` - Literal values

**Use cases:** Database IDs, national identifiers, reference numbers

---

#### Relationships
**File:** `relationships.ttl`

Shows how to model relationships between entities, including temporal constraints.

**Key concepts:**
- `ies:relationship` - Top-level relationship property
- Specialised relationships (works for, located in, etc.)
- Temporal relationships using States

**Use cases:** Organisational structures, associations, dependencies

---

#### Types and Classification
**File:** `types.ttl`

Demonstrates the use of `ClassOfElement` and powertype relationships for creating type hierarchies.

**Key concepts:**
- `ies:ClassOfElement` - Classes and categories
- `ies:powertype` - Type-level relationships
- `rdfs:subClassOf` - Class hierarchies
- `rdf:type` - Instance-of relationships

**Use cases:** Taxonomies, categorisation, type systems

---

### Complex Patterns

#### Communications
**File:** `communications.ttl`

Models communication events (calls, messages) with participants in sender and receiver roles.

**Key concepts:**
- `ies:VoiceCall` / `ies:Message` - Communication types
- `ies:Caller` / `ies:Callee` - Participant roles
- Bi-directional communication patterns

**Use cases:** Call records, messaging systems, communication logs

---

#### Event Linkages
**File:** `event-linkages.ttl`

Shows how events can be composed of or linked to other events.

**Key concepts:**
- `ies:isPartOf` - Part-whole relationships for events
- Event composition
- Sub-events and super-events

**Use cases:** Complex activities, workflows, project management

---

#### Geospatial
**File:** `geosparql.ttl`

Demonstrates geographic location using GeoSPARQL patterns.

**Key concepts:**
- `ies:GeoPoint` - Geographic points
- `ies:Latitude` / `ies:Longitude` - Coordinate identifiers
- Location-based queries

**Use cases:** Mapping, tracking, spatial analysis

---

#### Hospital Example
**File:** `hospital.ttl`

Comprehensive worked example of a patient's journey through hospital treatment.

**Key concepts:**
- `ies:PersonState` - States of the patient
- `ies:BoundingState` - Admission, discharge, treatment times
- `ies:Location` - Hospital facilities (wards, theatres)
- `ies:EventParticipant` - Participation in surgery

**Use cases:** Healthcare tracking, patient records, facility management

**Corresponds to:** [Introduction to IES - Hospital Example](../../user-guides/introduction.md#worked-example-fred-in-hospital)

---

#### Movement
**File:** `movement.ttl`

Models a person's journey involving multiple legs with different transport modes.

**Key concepts:**
- `ies:Journey` - End-to-end movement
- `ies:CarTravel` / `ies:Flight` - Transport modes
- `ies:Departure` / `ies:Arrival` - Bounding states
- `ies:VehicleUsed` - Asset participation

**Use cases:** Travel tracking, logistics, supply chain

---

#### Period of Time
**File:** `period-of-time.ttl`

Shows different ways to represent and use periods of time.

**Key concepts:**
- `ies:PeriodOfTime` - Temporal extents
- `ies:ParticularPeriod` - Specific time points
- ISO 8601 datetime encoding

**Use cases:** Scheduling, temporal reasoning, historical data

---

#### Sometimes (Discontinuous States)
**File:** `sometimes.ttl`

Demonstrates discontinuous states for modelling recurring or intermittent situations.

**Key concepts:**
- `ies:DiscontinuousState` - Non-contiguous temporal states
- "Usually" or "sometimes" patterns
- Temporal aggregation

**Use cases:** Parking patterns, seasonal activities, intermittent behaviours

---

#### When and Where
**File:** `when-and-where.ttl`

Combines temporal and spatial aspects for comprehensive spatio-temporal modelling.

**Key concepts:**
- `ies:inPeriod` - Temporal location
- `ies:inLocation` - Spatial location
- Combined spatio-temporal extent

**Use cases:** Event logging, audit trails, situational awareness

---

## Using These Samples

### Loading into an RDF Triple Store

**Apache Jena Fuseki:**
```bash
# Load a single sample
s-put http://localhost:3030/samples/data default hospital.ttl

# Load all samples
for file in *.ttl; do
  s-put http://localhost:3030/samples/data default "$file"
done
```

**GraphDB:**
```bash
# Import via GraphDB Workbench UI
# Or use RDF4J API programmatically
```

**Stardog:**
```bash
# Add sample data to database
stardog data add samples hospital.ttl movement.ttl communications.ttl
```

### Querying the Samples

**SPARQL Example - Find all people in the samples:**
```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX data: <http://informationexchangestandard.org/testdata#>

SELECT ?person ?name
WHERE {
    ?person a ies:Person .
    OPTIONAL { ?person ies:hasName ?nameRep .
               ?nameRep ies:representationValue ?name }
}
```

**SPARQL Example - Find events with participants:**
```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>

SELECT ?event ?participant ?entity
WHERE {
    ?event a ies:Event .
    ?participant ies:isParticipantIn ?event ;
                 ies:isParticipationOf ?entity .
}
```

### Validating Against IES Common

Ensure your instance data conforms to IES patterns:

```python
from rdflib import Graph

# Load ontology and instance data
ontology = Graph()
ontology.parse("../../specification/ies-common.ttl", format="turtle")

instance = Graph()
instance.parse("hospital.ttl", format="turtle")

# Combine for validation
combined = ontology + instance

# Perform SPARQL queries to check conformance
# Or use SHACL for formal validation
```

---

## Extending These Examples

These samples can serve as templates for your own IES data:

1. **Copy the relevant sample** that matches your use case
2. **Replace test data** (`data:` namespace) with your actual data
3. **Add domain-specific extensions** if needed (see [Extending IES](../../user-guides/extending-ies.md))
4. **Validate** against the IES Common ontology
5. **Load** into your RDF triple store or application

---

## Download All Samples

All sample files are available in the project repository:

**Repository structure:**
```
/
├── assessment.ttl
├── characteristics-and-measures.ttl
├── communications.ttl
├── event-linkages.ttl
├── event-participation.ttl
├── events.ttl
├── geosparql.ttl
├── hospital.ttl
├── identifiers.ttl
├── movement.ttl
├── period-of-time.ttl
├── relationships.ttl
├── sometimes.ttl
├── types.ttl
└── when-and-where.ttl
```

---

## Additional Resources

- [IES Examples Documentation](../ies-examples.md) - Detailed explanations with diagrams
- [User Guides](../../user-guides/) - How to create IES data
- [Instantiation Patterns](../../user-guides/instantiation-patterns.md) - Standard patterns for creating instances
- [IES Common Ontology](../../specification/ies-common.md) - Download the ontology

---

## Contributing Examples

If you have developed IES examples that demonstrate useful patterns or solve common problems, consider contributing them:

1. Ensure your example uses valid IES patterns
2. Add clear comments in the Turtle file
3. Provide a brief description of the use case
4. Submit via GitHub pull request

---

*© Crown Copyright 2020-2025 | Licensed under the MIT Licence*