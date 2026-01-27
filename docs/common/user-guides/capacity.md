# Capacity

A **Capacity** is a `ClassOfState` where all the members are classes that share the same Capacity that enables them (or is necessary at least in part) to perform some function as a participant in an `Event`.

The key insight is that a Capacity represents what an Element *can* do, whether or not it has ever actually done it. For example, an aircraft capable of Mach 2 has that Capacity even if it has never flown that fast and may never do so.

## The hasCapacity Relationship

The `hasCapacity` relationship asserts that an Element can have a particular instance of a Capacity. This is a "has a" relationship rather than an "is a" relationship, making it intuitive to express statements like "this building has the capacity to serve as an emergency shelter."

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# A building with two capacities
data:SandownCommunityHall a ies:Location ;
    ies:hasCapacity ex:OperateAsRecreationalSpace ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

## The eachHasCapacity Relationship

While `hasCapacity` asserts that a specific Element instance has a Capacity, `eachHasCapacity` asserts that all the instances of a certain class of `Elements` can have a particular `State`. This is useful for defining class-level capabilities in domain ontologies.

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# Class-level assertion: ALL fire stations can house emergency vehicles
ex:FireStation rdfs:subClassOf ies:Location ;
    ies:eachHasCapacity ex:HouseEmergencyVehicles ;
    ies:eachHasCapacity ex:ProvideFirstAid .

# Instance-level assertion: THIS specific hall can shelter people
data:SandownCommunityHall a ies:Location ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

### When to Use Each Property

| Property | Use When... |
|----------|-------------|
| `hasCapacity` | A specific Element has been assessed or designated as having a Capacity |
| `eachHasCapacity` | All members of a class have a Capacity |

### Combining Class and Instance Capacities

Instances can have both inherited class-level Capacities (via `eachHasCapacity` on their class) and additional instance-specific Capacities (via `hasCapacity` on the instance):
```turtle
# Southsea Fire Station is a FireStation (so inherits HouseEmergencyVehicles)
# AND has been specifically designated as an emergency shelter
data:SouthseaFireStation a ex:FireStation ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

## Relationship to Existing Patterns

IES has existing concepts for modelling capabilities and tendencies through `DispositionalClass`, `Capability`, and `Tendency`. These use an "is a" pattern via `rdf:type`.

The Capacity pattern provides an alternative "has a" approach using `hasCapacity`. Both patterns remain valid in IES:

- The existing `DispositionalClass` pattern is **retained for backwards compatibility**
- The new `Capacity` pattern is **additive and non-breaking**
- Implementers may choose whichever pattern better fits their data and use cases

The Capacity pattern is recommended for new implementations because:

- It aligns more naturally with how we describe capabilities in everyday language
- It provides clearer spatio-temporal semantics (via `State` and `ClassOfState`)
- It separates the concept of having a Capacity from actually using it in Event participation
- It supports conditional capacities (e.g., "can fly at Mach 2 *only* when in an operational state")

## Creating Domain-Specific Capacity Taxonomies

The core IES ontology defines `ies:Capacity`, `ies:hasCapacity`, and `ies:eachHasCapacity`. Domain-specific applications should create their own taxonomies of Capacity instances relevant to their use cases.

For example, an emergency planning domain might define:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .

# Domain-specific Capacity instances
ex:ShelterDisplacedPersons a ies:Capacity ;
    rdfs:label "Shelter Displaced Persons"@en-gb ;
    rdfs:comment "The capacity to provide emergency shelter for displaced persons."@en-gb .

ex:DistributePotableWater a ies:Capacity ;
    rdfs:label "Distribute Potable Water"@en-gb ;
    rdfs:comment "The capacity to serve as a distribution point for potable water."@en-gb .

ex:DisseminateInformation a ies:Capacity ;
    rdfs:label "Disseminate Information"@en-gb ;
    rdfs:comment "The capacity to serve as an information hub for public communications."@en-gb .

ex:AssessLocationsForEmergencyPlanning a ies:Capacity ;
    rdfs:label "Assess Locations for Emergency Planning"@en-gb ;
    rdfs:comment "The capacity to conduct emergency planning assessments of locations."@en-gb .
```

## Capacities and States

An Element can have a Capacity at the whole-life level, meaning the Entity (as a State) always has this potential, or at the State level (the Element has this Capacity only during certain periods).

When an Element actually *uses* its Capacity, this is modelled as a State of that Element participating in an Event. The State is typed as both an `EventParticipant` and as a member of the relevant Capacity class.

```turtle
# The Location has the Capacity (potential)
data:CarPark a ies:Location ;
    ies:hasCapacity ex:DistributePotableWater .

# An Event where the Capacity is actually being used
data:WaterDistributionOperation a ies:Event ;
    rdfs:label "Water Distribution Operation"@en-gb .

# A State of the Location when it is actively distributing water
data:CarParkDistributingWater a ies:EventParticipant, ex:DistributePotableWater ;
    ies:isParticipationOf data:CarPark ;
    ies:isParticipantIn data:WaterDistributionOperation .
```

This separation of "having a Capacity" that is latent (or unused) from "using a Capacity" is a key feature of the pattern. For example, it supports queries like, "Which Locations have the Capacity to serve as emergency shelters?" versus "Which Locations have actually served as emergency shelters during incidents?".

## Worked Example: Emergency Shelter

This example demonstrates a community hall that has the Capacity to serve as an emergency shelter. It shows:

1. The building being assessed as having this Capacity
2. The building operating normally as a recreational space
3. The building being activated as an emergency shelter during an incident

### The Location and Its Capacities

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# The entity that is Sandown Community Hall
data:SandownCommunityHall a ies:Location ;
    rdfs:label "Sandown Community Hall"@en-gb ;
    rdfs:comment "Community sports and events venue in Sandown"@en-gb ;
    ies:hasCapacity ex:OperateAsRecreationalSpace ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

### The Assessment

An organisation assesses the building's suitability as an emergency shelter:

```turtle
# An organisation that carries out emergency planning assessments
data:AcmeLtd a ies:Organisation ;
    rdfs:label "Acme Ltd"@en-gb ;
    ies:hasCapacity ex:AssessLocationsForEmergencyPlanning .

# The emergency planning assessment
data:EmergencyPlanningAssessment a ies:Assessment ;
    rdfs:label "Emergency Planning Assessment"@en-gb .

# The start of the assessment
data:AssessmentStart a ies:BoundingState ;
    ies:isStartOf data:EmergencyPlanningAssessment ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "20240101T120000Z"@en-gb ] .

# The end of the assessment
data:AssessmentEnd a ies:BoundingState ;
    ies:isEndOf data:EmergencyPlanningAssessment ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "20240131T120000Z"@en-gb ] .

# A State of Acme Ltd performing the assessment
data:AcmeAssessing a ies:Assessor, ex:AssessLocationsForEmergencyPlanning ;
    ies:isParticipationOf data:AcmeLtd ;
    ies:isParticipantIn data:EmergencyPlanningAssessment .
```

### Normal Operations

The building operates as a recreational space during normal times:

```turtle
# An event where the hall is operating as a recreational space
data:RecreationalOperation a ies:Event ;
    rdfs:label "Recreational Space Operation"@en-gb .

# The period of normal operation
data:RecreationalStart a ies:BoundingState ;
    ies:isStartOf data:RecreationalOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "2024-01-01T12:00:00"^^xsd:dateTime ] .

data:RecreationalEnd a ies:BoundingState ;
    ies:isEndOf data:RecreationalOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "2024-12-31T12:00:00"^^xsd:dateTime ] .

# A State of the hall actually operating as a recreational centre
data:HallAsRecreationalSpace a ies:EventParticipant, ex:OperateAsRecreationalSpace ;
    ies:isParticipationOf data:SandownCommunityHall ;
    ies:isParticipantIn data:RecreationalOperation .
```

### Emergency Activation

When an incident occurs, the building is activated as an emergency shelter:

```turtle
# An event where the hall is operating as an emergency shelter
data:EmergencyShelterOperation a ies:Event ;
    rdfs:label "Emergency Shelter Operation"@en-gb .

# The period of emergency operation
data:ShelterStart a ies:BoundingState ;
    ies:isStartOf data:EmergencyShelterOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "2025-01-01T12:00:00"^^xsd:dateTime ] .

data:ShelterEnd a ies:BoundingState ;
    ies:isEndOf data:EmergencyShelterOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; rdfs:label "2025-01-31T12:00:00"^^xsd:dateTime ] .

# A State of the hall actually operating as an emergency shelter
data:HallAsShelter a ies:EventParticipant, ex:ShelterDisplacedPersons ;
    ies:isParticipationOf data:SandownCommunityHall ;
    ies:isParticipantIn data:EmergencyShelterOperation .
```

## Querying Capacities

The Capacity pattern enables useful queries. Here are some examples using SPARQL:

### Finding Entities with a Specific Capacity

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex: <http://example.com/ontology#>

SELECT ?entity ?label
WHERE {
    ?entity ies:hasCapacity ex:ShelterDisplacedPersons ;
            rdfs:label ?label .
}
```

### Finding When a Capacity Was Actually Used

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex: <http://example.com/ontology#>

SELECT ?entity ?event ?startTime
WHERE {
    ?state a ex:ShelterDisplacedPersons ;
           ies:isParticipationOf ?entity ;
           ies:isParticipantIn ?event .
    ?startBound ies:isStartOf ?event ;
                ies:inPeriod ?period .
    ?period rdfs:label ?startTime .
}
```

## Summary

The Capacity pattern in IES provides:

- A clear way to express what an Element *can* do (potential)
- Separation between having a Capacity and using it (actuality)
- Support for assessments of Capacities
- Temporal tracking of when Capacities are activated
- A foundation for domain-specific Capacity taxonomies

### Key Principles

1. **Capacity is potential** — an Element can have a Capacity without ever using it
2. **hasCapacity is a "has a" relationship** — more intuitive than "is a" typing
3. **States use Capacities** — when a Capacity is actually employed, it's modelled as Event participation
4. **Domain taxonomies are expected** — IES provides the framework; applications define specific Capacities
5. **Backwards compatible** — the existing `DispositionalClass` pattern remains valid

---

## Related Documentation

- [Instantiation Patterns](instantiation-patterns.md) — Standard patterns for creating IES data
- [4D Ontology Approach](4d-ontology.md) — Understanding States and temporal parts
- [Extending IES](extending-ies.md) — How to create domain-specific extensions

---

*© Crown Copyright 2020-2026*
