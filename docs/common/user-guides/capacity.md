# Capacity

A **Capacity** is a `ClassOfState` representing what a State of an Entity *can* do (in some possible world), whether or not it has ever actually done it.

The key insight is that a Capacity represents modal possibility: a State *can* be a member of a particular `ClassOfState` in some possible world. For example, a State of "Fighter XYZ-123 in operational condition" can be a member of "Performer of Mach 2 flight" even if that specific aircraft has never actually flown at Mach 2.

## The hasCapacity Relationship

The `hasCapacity` relationship asserts that a **State** can have (be a member of) a particular `ClassOfState` (Capacity). This is a "has a" relationship rather than an "is a" relationship, making it intuitive to express statements like "this building, during the emergency planning period, has the capacity to serve as an emergency shelter."

**Property signature:**
- **Domain:** `ies:State` 
- **Range:** `ies:ClassOfState`

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# The whole-life Entity
data:SandownCommunityHall a ies:Location ;
    rdfs:label "Sandown Community Hall"@en-gb .

# A State of that Location during the planning period
data:HallDuringPlanning a ies:LocationState ;
    rdfs:label "Hall during 2024 planning"@en-gb ;
    ies:isStateOf data:SandownCommunityHall ;
    ies:inPeriod data:Period2024 ;
    # This State has two capacities
    ies:hasCapacity ex:OperateAsRecreationalSpace ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

## The eachHasCapacity Relationship

While `hasCapacity` asserts that a specific State instance has a Capacity, `eachHasCapacity` asserts that all members of a `ClassOfState` can have a particular Capacity. This is useful for defining class-level capabilities in domain ontologies.

**Property signature:**
- **Domain:** `ies:ClassOfState`
- **Range:** `ies:ClassOfState`
```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# Class-level assertion: ALL Eurofighters in operational condition can fly at Mach 2
ex:EurofighterInOperationalCondition a ies:ClassOfState ;
    rdfs:subClassOf ies:VehicleState ;
    ies:eachHasCapacity ex:PerformerOfMach2Flight .

# Instance-level assertion: THIS specific Eurofighter State can fly at Mach 2
# (inherits the capacity from its class via eachHasCapacity)
data:FighterXYZ123InOpsCondition2024 a ies:VehicleState, ex:EurofighterInOperationalCondition ;
    rdfs:label "Fighter XYZ-123 in operational condition (2024)"@en-gb ;
    ies:isStateOf data:FighterXYZ123 ;
    ies:inPeriod data:Period2024 .
    # Inherits the Mach 2 capacity from ex:EurofighterInOperationalCondition
```

### When to Use Each Property

| Property | Use When... | Example |
|----------|-------------|---------|
| `hasCapacity` | A specific State instance has been assessed or designated as having a Capacity | "Fighter XYZ-123 in operational condition during 2024 has the capacity to fly at Mach 2" |
| `eachHasCapacity` | All members of a ClassOfState have a Capacity | "Every Eurofighter in operational condition has the capacity to fly at Mach 2" |

### Combining Class and Instance Capacities

States can have both inherited class-level Capacities (via `eachHasCapacity` on their class) and additional instance-specific Capacities (via `hasCapacity` on the State):
```turtle
# Define a class-level capacity: ALL community halls can operate as recreational spaces
ex:CommunityHallInOperation a ies:ClassOfState ;
    rdfs:subClassOf ies:LocationState ;
    ies:eachHasCapacity ex:OperateAsRecreationalSpace .

# A specific State inherits the class capacity AND has an additional one
data:SandownHallDuring2024 a ies:LocationState, ex:CommunityHallInOperation ;
    rdfs:label "Sandown Community Hall during 2024"@en-gb ;
    ies:isStateOf data:SandownCommunityHall ;
    ies:inPeriod data:Period2024 ;
    # Inherits OperateAsRecreationalSpace from ex:CommunityHallInOperation
    # Plus has an instance-specific capacity (assessed for this specific hall):
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

## Modelling Whole-Life vs Temporal Capacities

**Important:** Even when a capacity appears to persist throughout an Entity's existence, it is still modelled as a State having the capacity, not the Entity directly.

### Temporal Capacity (capacity during specific period)

```turtle
# A car park assessed in 2024 as having water distribution capacity
data:CarParkDuringPlanning a ies:LocationState ;
    ies:isStateOf data:SandownCarPark ;
    ies:inPeriod data:Period2024 ;
    ies:hasCapacity ex:DistributePotableWater .
```

### Whole-Life Capacity (capacity throughout Entity's existence)

For capacities that persist throughout an Entity's existence, IES provides a convenient pattern: Entity subclasses are also subclasses of their corresponding State subclass (e.g., `ies:Person rdfs:subClassOf ies:PersonState`, `ies:Location rdfs:subClassOf ies:LocationState`).

**Exception:** `ies:Entity` itself is NOT a subclass of `ies:State`.

This means when you instantiate a specific Entity subclass (like Person or Location), that instance is automatically both an Entity and a State representing its whole life:
```turtle
# A fire station that has always been able to house emergency vehicles
# Because Location is a subclass of LocationState, this instance is BOTH
data:PortsmouthFireStation a ies:Location ;  # Therefore also a LocationState
    rdfs:label "Portsmouth Fire Station"@en-gb ;
    # Can attach capacity directly - no need for separate State instance
    ies:hasCapacity ex:HouseEmergencyVehicles .
```

This pattern works for:
- `ies:Person` instances (also `PersonState`)
- `ies:Location` instances (also `LocationState`)
- `ies:Vehicle` instances (also `VehicleState`)
- And other Entity subclasses that follow this pattern

For temporal capacities (capacities during specific periods), you still create explicit State instances with temporal bounds as shown in the previous section.

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

**Note:** Typing a `ClassOfState` as `ies:Capacity` is optional but recommended for semantic clarity. The properties accept any `ClassOfState` as their range.

For example, an emergency planning domain might define:

```turtle
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .

# Domain-specific Capacity instances (subclasses of both ClassOfState and Capacity)
ex:ShelterDisplacedPersons a ies:Capacity ;
    rdfs:label "Shelter Displaced Persons"@en-gb ;
    rdfs:comment "The capacity to provide emergency shelter for displaced persons."@en-gb ;
    rdfs:subClassOf ies:EventParticipant .

ex:DistributePotableWater a ies:Capacity ;
    rdfs:label "Distribute Potable Water"@en-gb ;
    rdfs:comment "The capacity to serve as a distribution point for potable water."@en-gb ;
    rdfs:subClassOf ies:EventParticipant .

ex:AssessLocationsForEmergencyPlanning a ies:Capacity ;
    rdfs:label "Assess Locations for Emergency Planning"@en-gb ;
    rdfs:comment "The capacity to conduct emergency planning assessments of locations."@en-gb ;
    rdfs:subClassOf ies:EventParticipant .
```

## Capacities and Actualisation

Having a Capacity is distinct from *using* that Capacity. When a State actually uses its Capacity, this is modelled as that State participating in an Event and being a member (via `rdf:type`) of the Capacity class.

```turtle
# A State of the car park during planning - HAS the capacity (potential)
data:CarParkDuringPlanning a ies:LocationState ;
    ies:isStateOf data:SandownCarPark ;
    ies:inPeriod data:Period2024 ;
    ies:hasCapacity ex:DistributePotableWater .

# An Event where water is being distributed
data:WaterDistributionOperation a ies:Event ;
    rdfs:label "Water Distribution Operation"@en-gb .

# A State of the car park actually distributing water - USES the capacity (actual)
data:CarParkDistributingWater a ies:EventParticipant, ex:DistributePotableWater ;
    rdfs:comment "The car park actualising its capacity"@en-gb ;
    ies:isParticipationOf data:SandownCarPark ;
    ies:isParticipantIn data:WaterDistributionOperation .
```

**Key distinction:**
- `ies:hasCapacity` = "can be a member of this ClassOfState" (modal possibility)
- `rdf:type` = "is a member of this ClassOfState" (actuality)

This separation enables queries like:
- "Which Locations **have the Capacity** to serve as emergency shelters?" (potential resources)
- "Which Locations **have actually served** as emergency shelters?" (actual usage)

## Worked Example: Emergency Shelter

This example demonstrates a community hall that has the Capacity to serve as an emergency shelter. It shows:

1. The building being assessed as having this Capacity
2. The building operating normally as a recreational space
3. The building being activated as an emergency shelter during an incident

### The Location and Its Assessed Capacities

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex: <http://example.com/ontology#> .
@prefix data: <http://example.com/data#> .

# The whole-life Entity
data:SandownCommunityHall a ies:Location ;
    rdfs:label "Sandown Community Hall"@en-gb ;
    rdfs:comment "Community sports and events venue in Sandown"@en-gb .

# A State of the hall during the 2024 planning period
data:HallDuringPlanning a ies:LocationState ;
    rdfs:label "Hall during 2024 planning period"@en-gb ;
    ies:isStateOf data:SandownCommunityHall ;
    ies:inPeriod data:Period2024 ;
    # These are the capacities identified during assessment
    ies:hasCapacity ex:OperateAsRecreationalSpace ;
    ies:hasCapacity ex:ShelterDisplacedPersons .
```

### The Assessment

An organisation assesses the building's suitability as an emergency shelter:

```turtle
# An organisation that carries out assessments
data:AcmeLtd a ies:Organisation ;
    rdfs:label "Acme Ltd"@en-gb .

# A State of Acme during the planning period
data:AcmeDuringPlanning a ies:OrganisationState ;
    ies:isStateOf data:AcmeLtd ;
    ies:inPeriod data:Period2024 ;
    ies:hasCapacity ex:AssessLocationsForEmergencyPlanning .

# The emergency planning assessment
data:EmergencyPlanningAssessment a ies:Assessment ;
    rdfs:label "Emergency Planning Assessment"@en-gb .

# Bounding states for the assessment
data:AssessmentStart a ies:BoundingState ;
    ies:isStartOf data:EmergencyPlanningAssessment ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2024-01-01T12:00:00Z"^^xsd:string ] .

data:AssessmentEnd a ies:BoundingState ;
    ies:isEndOf data:EmergencyPlanningAssessment ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2024-01-31T12:00:00Z"^^xsd:string ] .

# A State of Acme actually performing the assessment (actualising its capacity)
data:AcmeAssessing a ies:Assessor, ex:AssessLocationsForEmergencyPlanning ;
    rdfs:comment "Acme actualising its assessment capacity"@en-gb ;
    ies:isParticipationOf data:AcmeLtd ;
    ies:isParticipantIn data:EmergencyPlanningAssessment .
```

### Normal Operations

The building operates as a recreational space during normal times:

```turtle
# An event where the hall is operating as a recreational space
data:RecreationalOperation a ies:Event ;
    rdfs:label "Recreational Space Operation"@en-gb .

# Bounding states for normal operation
data:RecreationalStart a ies:BoundingState ;
    ies:isStartOf data:RecreationalOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2024-01-01T12:00:00"^^xsd:string ] .

data:RecreationalEnd a ies:BoundingState ;
    ies:isEndOf data:RecreationalOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2024-12-31T12:00:00"^^xsd:string ] .

# A State of the hall actually operating as a recreational centre (actualising capacity)
data:HallAsRecreationalSpace a ies:EventParticipant, ex:OperateAsRecreationalSpace ;
    rdfs:comment "Hall actualising its recreational capacity"@en-gb ;
    ies:isParticipationOf data:SandownCommunityHall ;
    ies:isParticipantIn data:RecreationalOperation .
```

### Emergency Activation

When an incident occurs, the building is activated as an emergency shelter:

```turtle
# An event where the hall is operating as an emergency shelter
data:EmergencyShelterOperation a ies:Event ;
    rdfs:label "Emergency Shelter Operation"@en-gb .

# Bounding states for emergency operation
data:ShelterStart a ies:BoundingState ;
    ies:isStartOf data:EmergencyShelterOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2025-01-01T12:00:00"^^xsd:string ] .

data:ShelterEnd a ies:BoundingState ;
    ies:isEndOf data:EmergencyShelterOperation ;
    ies:inPeriod [ a ies:ParticularPeriod ; 
                   ies:iso8601PeriodRepresentation "2025-01-31T12:00:00"^^xsd:string ] .

# A State of the hall actually operating as an emergency shelter (actualising capacity)
data:HallAsShelter a ies:EventParticipant, ex:ShelterDisplacedPersons ;
    rdfs:comment "Hall actualising its emergency shelter capacity"@en-gb ;
    ies:isParticipationOf data:SandownCommunityHall ;
    ies:isParticipantIn data:EmergencyShelterOperation .
```

## Querying Capacities

The Capacity pattern enables useful queries. Here are some examples using SPARQL:

### Finding Entities with States That Have a Specific Capacity

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex: <http://example.com/ontology#>

SELECT ?entity ?entityLabel ?state
WHERE {
    ?state ies:hasCapacity ex:ShelterDisplacedPersons ;
           ies:isStateOf ?entity .
    ?entity rdfs:label ?entityLabel .
}
```

### Finding When a Capacity Was Actually Used

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex: <http://example.com/ontology#>

SELECT ?entity ?event ?startTime
WHERE {
    # Find States that are members of the Capacity class (actualisation)
    ?state a ex:ShelterDisplacedPersons ;
           ies:isParticipationOf ?entity ;
           ies:isParticipantIn ?event .
    ?startBound ies:isStartOf ?event ;
                ies:inPeriod ?period .
    ?period ies:iso8601PeriodRepresentation ?startTime .
}
```

### Finding Unused Capacities

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex: <http://example.com/ontology#>

SELECT ?entity ?entityLabel
WHERE {
    # States that HAVE the capacity
    ?state ies:hasCapacity ex:ShelterDisplacedPersons ;
           ies:isStateOf ?entity .
    ?entity rdfs:label ?entityLabel .
    
    # But have never actualised it
    FILTER NOT EXISTS {
        ?actualState a ex:ShelterDisplacedPersons ;
                     ies:isParticipationOf ?entity .
    }
}
```

## Summary

The Capacity pattern in IES provides:

- A clear way to express what a State of an Entity *can* do (modal possibility)
- Separation between having a Capacity and actualising it
- Support for assessments of Capacities
- Temporal tracking of when Capacities are activated
- A foundation for domain-specific Capacity taxonomies

### Key Principles

1. **Capacity is modal possibility** — a State can have a Capacity without ever actualising it
2. **hasCapacity domain is State** — capacities attach to temporal parts
3. **Actualisation via rdf:type** — when a Capacity is actually employed, the State is a member of the Capacity class
4. **Whole-life capacities use Entity instances** — Entity subclass instances (Person, Location, etc.) are also States representing their whole life
5. **Domain taxonomies expected** — IES provides the framework; applications define specific Capacities
6. **Optional typing as ies:Capacity** — provides semantic clarity but is not mandatory

---

## Related Documentation

- [Instantiation Patterns](instantiation-patterns.md) — Standard patterns for creating IES data
- [4D Ontology Approach](4d-ontology.md) — Understanding States and temporal parts
- [Extending IES](extending-ies.md) — How to create domain-specific extensions

---

*© Crown Copyright 2020-2026*
