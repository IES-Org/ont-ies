# Dispositions

A **disposition** is what a State of an Entity *can* do — its potential — in some possible world, whether or not it has ever actually done it.

The key insight is that a disposition represents modal possibility: a State *can* be a member of a particular `ClassOfState` in some possible world. For example, a State of "Fighter XYZ-123 in operational condition" can be a member of "Performer of Mach 2 flight" even if that specific aircraft has never actually flown at Mach 2.

Dispositions in IES are expressed by asserting that a State (or a class of States) is related to a `ClassOfState` — the class representing the potential behaviour or role. The `ClassOfState` used as a disposition target is typically an instance of `ies:DispositionalClass`, or one of its sub-classes `ies:Capability` (a shared capability) or `ies:Tendency` (a shared tendency).

## The Existing Encoding: `allHaveDisposition` and `isDisposedTo`

IES has two existing properties for recording dispositions.

`ies:allHaveDisposition` asserts that all instances of a `ClassOfElement` share a disposition. It is a sub-property of `rdfs:subClassOf`, so it carries a structural inference: if `ex:Eurofighter ies:allHaveDisposition ex:FlyAtMach2`, a reasoner infers `ex:Eurofighter rdfs:subClassOf ex:FlyAtMach2` — placing the Entity class *within* the Capability hierarchy.

`ies:isDisposedTo` asserts that an individual `Element` is a member of a `DispositionalClass`. It is a sub-property of `rdf:type`, so it carries a type inference: if `data:FighterXYZ-123 ies:isDisposedTo ex:FlyAtMach2`, a reasoner infers `data:FighterXYZ-123 rdf:type ex:FlyAtMach2`.

Both properties remain valid in IES v5 and are retained for backwards compatibility.

## Two New Properties: `hasDisposition` and `eachHasDisposition`

IES v5.1 introduces two complementary properties that express disposition without the sub-class and type inferences of the existing properties.

**Property signatures:**

| Property | Domain | Range | Level |
|---|---|---|---|
| `ies:hasDisposition` | `ies:State` | `ies:ClassOfState` | Individual State |
| `ies:eachHasDisposition` | `ies:ClassOfState` | `ies:ClassOfState` | Class of States |

These properties are sub-properties of `ies:relationship` (not of `rdf:type` or `rdfs:subClassOf`), so they record the modal relationship directly without altering the type hierarchy.

### `ies:hasDisposition`

`hasDisposition` asserts that a specific State instance can have (be a member of) a particular `ClassOfState`. This expresses modal possibility: the State *can* be a member of the specified class, but need not actually be one.

The domain is `ies:State`. In practice, this covers:

- **Explicit temporal States**, such as `data:FighterXYZ-123-Operational-2024 a ies:VehicleState`
- **Whole-life Entity instances**, such as `data:FighterXYZ-123 a ies:Aircraft`, because every IES Entity subclass (Aircraft, Person, Location, Organisation, etc.) is also a sub-class of its corresponding State subclass through the Entity-as-State pattern

```turtle
@prefix ies: <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex:  <http://example.org/mil#> .
@prefix data: <http://example.org/mil/data#> .

# Individual-level assertion on a temporal State
data:FighterXYZ-123-Operational-2024 a ies:VehicleState ;
    rdfs:label "Fighter XYZ-123 in operational condition (2024)"@en-GB ;
    ies:isStateOf data:FighterXYZ-123 ;
    ies:inPeriod data:Period2024 ;
    ies:hasDisposition ex:FlyAtMach2 .
```

The range is `ies:ClassOfState`. The target class is typically an instance of `ies:Capability` or `ies:Tendency`:

```turtle
ex:FlyAtMach2 a ies:Capability ;
    rdfs:label "Fly at Mach 2"@en-GB ;
    rdfs:subClassOf ies:VehicleState .
```

### `ies:eachHasDisposition`

`eachHasDisposition` asserts that *every member* of a `ClassOfState` can have (be a member of) another `ClassOfState`. This is a universal assertion over a class rather than a statement about any individual.

```turtle
# Class-level assertion: ALL Eurofighters in operational condition can fly at Mach 2
ex:EurofighterInOperationalCondition a ies:ClassOfState ;
    rdfs:label "Eurofighter in operational condition"@en-GB ;
    rdfs:subClassOf ies:VehicleState ;
    ies:eachHasDisposition ex:FlyAtMach2 .
```

Because `eachHasDisposition` is not a sub-property of `rdfs:subClassOf`, the class `ex:EurofighterInOperationalCondition` is **not** placed within the Capability hierarchy. The asset class and the Capability remain structurally separate, connected only by the `eachHasDisposition` arc. A reasoner will not infer that every member of `ex:EurofighterInOperationalCondition` is a member of `ex:FlyAtMach2` — only that they *can* be.

### When to Use Each Property

| Property | Use When… | Example |
|---|---|---|
| `hasDisposition` | A specific State instance can have a particular disposition | "Fighter XYZ-123 in operational condition during 2024 can fly at Mach 2" |
| `eachHasDisposition` | Every member of a `ClassOfState` can have a particular disposition | "Every Eurofighter in operational condition can fly at Mach 2" |
| `isDisposedTo` | An Element is asserted to be a member of a `DispositionalClass` (type inference intended) | Existing data using the original pattern |
| `allHaveDisposition` | All instances of a `ClassOfElement` share a disposition (subclass inference intended) | Existing data using the original pattern |

### Choosing Between the Old and New Properties

The key structural difference is the presence or absence of type and subclass inferences:

- `isDisposedTo` and `allHaveDisposition` place subjects *within* the `DispositionalClass` hierarchy via `rdf:type` and `rdfs:subClassOf` inferences respectively.
- `hasDisposition` and `eachHasDisposition` record the modal relationship without altering the type hierarchy — the subject and the disposition target remain structurally separate.

For new implementations, `hasDisposition` and `eachHasDisposition` are recommended because:

- The modal commitment (the State *can* be a member of the class) sits in the property, not in an incidental type inference
- The `ClassOfState` domain/range aligns naturally with 4D extensional modelling, where whole-life Entities and explicit temporal States are uniformly treated as States
- Asset classes and Capability classes remain compositionally independent

The existing `isDisposedTo` and `allHaveDisposition` properties are retained for backwards compatibility and remain valid for data that intentionally uses the type/subclass encoding.

## Conditional Dispositions

Dispositions are often conditional: an asset may be capable of something only when in a particular state (e.g., Mach 2 flight only when in operational condition). The recommended approach is to define a conditional `ClassOfState` representing the subset of interest, and attach the disposition to that class:

```turtle
# The disposition target
ex:FlyAtMach2 a ies:Capability ;
    rdfs:label "Fly at Mach 2"@en-GB ;
    rdfs:subClassOf ies:VehicleState .

# A conditional ClassOfState: Eurofighters in operational condition
ex:EurofighterInOperationalCondition a ies:ClassOfState ;
    rdfs:label "Eurofighter in operational condition"@en-GB ;
    rdfs:subClassOf ies:VehicleState ;
    ies:eachHasDisposition ex:FlyAtMach2 .

# A temporal State of the specific aircraft, typed as that conditional class
data:FighterXYZ-123-Operational-2024 a ex:EurofighterInOperationalCondition ;
    rdfs:label "Fighter XYZ-123 in operational condition (2024)"@en-GB ;
    ies:isStateOf data:FighterXYZ-123 ;
    ies:inPeriod data:Period2024 ;
    ies:hasDisposition ex:FlyAtMach2 .
```

This approach keeps Capabilities compositional: the Capability, the precondition, and their relationship are all machine-readable. A Eurofighter with a failed engine remains a member of the class `ex:Eurofighter` but is not currently a member of `ex:EurofighterInOperationalCondition` — and therefore does not inherit the Mach 2 disposition from the class-level assertion, while still retaining any individual-level `hasDisposition` assertions made about it.

## Modelling Whole-Life vs Temporal Dispositions

Because every Entity subclass (e.g. `ies:Aircraft`, `ies:Person`, `ies:Location`) is also a sub-class of its corresponding State subclass (e.g. `ies:VehicleState`, `ies:PersonState`, `ies:LocationState`), a whole-life Entity instance satisfies the `ies:State` domain of `hasDisposition` directly. No separate State instance is needed for dispositions that apply throughout an Entity's existence:

```turtle
# Whole-life disposition — no separate State instance needed
data:FighterXYZ-123 a ies:Aircraft ;
    rdfs:label "Fighter XYZ-123"@en-GB ;
    ies:hasDisposition ex:FlyAtMach2 .
```

For dispositions that hold only during a specific period, create an explicit State instance with temporal bounds:

```turtle
# Temporal disposition — State instance with period
data:FighterXYZ-123-PostMaint-2024 a ies:VehicleState ;
    rdfs:label "Fighter XYZ-123 post-maintenance (2024)"@en-GB ;
    ies:isStateOf data:FighterXYZ-123 ;
    ies:inPeriod data:Period2024 ;
    ies:hasDisposition ex:FlyAtMach2 .
```

> **Note.** `ies:Entity` itself is **not** a sub-class of `ies:State`, so the pattern applies only to concrete Entity subclasses (Aircraft, Person, Location, Organisation, etc.), not to bare `ies:Entity` instances.

## Disposition and Actualisation

Having a disposition is distinct from *using* it. When a State actually exercises its disposition, this is modelled as that State participating in an Event and being typed as a member of the disposition's `ClassOfState`:

```turtle
# A State of the aircraft — HAS the disposition (potential)
data:FighterXYZ-123-Operational-2024 a ies:VehicleState ;
    ies:isStateOf data:FighterXYZ-123 ;
    ies:inPeriod data:Period2024 ;
    ies:hasDisposition ex:FlyAtMach2 .

# An Event of Mach 2 flight
data:Sortie20240717 a ies:Event ;
    rdfs:label "Sortie 20240717"@en-GB .

# A State of the aircraft during the sortie — IS a member of the class (actuality)
data:FighterXYZ-123-Flying-20240717 a ex:FlyAtMach2 ;
    rdfs:comment "Fighter XYZ-123 actualising its Mach 2 disposition"@en-GB ;
    ies:isParticipationOf data:FighterXYZ-123 ;
    ies:isParticipantIn data:Sortie20240717 .
```

**Key distinction:**

- `ies:hasDisposition` = "can be a member of this `ClassOfState`" (modal possibility)
- `rdf:type` = "is a member of this `ClassOfState`" (actuality)

This separation enables queries such as:

- "Which aircraft **have the disposition** to fly at Mach 2?" (potential — readiness assessment)
- "Which aircraft **have actually flown** at Mach 2?" (actuality — operational record)

## Querying Dispositions

### Finding all States with a given disposition

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex:  <http://example.org/mil#>

SELECT ?state ?entity
WHERE {
    ?state ies:hasDisposition ex:FlyAtMach2 .
    OPTIONAL { ?state ies:isStateOf ?entity }
}
```

### Finding all classes whose members have a given disposition

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex:  <http://example.org/mil#>

SELECT ?class ?classLabel
WHERE {
    ?class ies:eachHasDisposition ex:FlyAtMach2 ;
           rdfs:label ?classLabel .
}
```

### Finding assets with a disposition that have never actualised it

```sparql
PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
PREFIX ex:  <http://example.org/mil#>

SELECT ?entity ?entityLabel
WHERE {
    ?state ies:hasDisposition ex:FlyAtMach2 ;
           ies:isStateOf ?entity .
    ?entity rdfs:label ?entityLabel .
    FILTER NOT EXISTS {
        ?actualState a ex:FlyAtMach2 ;
                     ies:isParticipationOf ?entity .
    }
}
```

## Worked Example: Fighter XYZ-123

This example brings together class-level and individual-level dispositions for a Eurofighter, showing how the two properties interact and how a disposition is later actualised.

### Domain Vocabulary

```turtle
@prefix ies:  <http://informationexchangestandard.org/ont/ies/common/> .
@prefix ex:   <http://example.org/mil#> .
@prefix data: <http://example.org/mil/data#> .

# Disposition target
ex:FlyAtMach2 a ies:Capability ;
    rdfs:label "Fly at Mach 2"@en-GB ;
    rdfs:subClassOf ies:VehicleState .

# Conditional ClassOfState — only Eurofighters in operational condition
ex:EurofighterInOperationalCondition a ies:ClassOfState ;
    rdfs:label "Eurofighter in operational condition"@en-GB ;
    rdfs:subClassOf ies:VehicleState ;
    ies:eachHasDisposition ex:FlyAtMach2 .   # class-level assertion
```

### Individual Aircraft and Temporal State

```turtle
# The whole-life aircraft Entity
data:FighterXYZ-123 a ies:Aircraft ;
    rdfs:label "Fighter XYZ-123"@en-GB .

# A post-maintenance State — the aircraft has been assessed in operational condition
data:FighterXYZ-123-Operational-2024 a ex:EurofighterInOperationalCondition ;
    rdfs:label "Fighter XYZ-123 in operational condition (2024)"@en-GB ;
    ies:isStateOf data:FighterXYZ-123 ;
    ies:inPeriod data:Period2024 ;
    ies:hasDisposition ex:FlyAtMach2 .   # individual-level assertion
```

Here `data:FighterXYZ-123-Operational-2024` has the disposition both by direct `hasDisposition` assertion *and* by virtue of being a member of `ex:EurofighterInOperationalCondition` (which carries `eachHasDisposition ex:FlyAtMach2`). An implementation may rely on the class-level assertion alone, or assert both for clarity.

### Actualisation

```turtle
# A sortie in which Mach 2 is actually achieved
data:Sortie20240717 a ies:Event ;
    rdfs:label "Sortie 20240717"@en-GB .

data:SortieStart a ies:BoundingState ;
    ies:isStartOf data:Sortie20240717 ;
    ies:inPeriod [ a ies:ParticularPeriod ;
                   ies:iso8601PeriodRepresentation "2024-07-17T09:00:00Z"^^xsd:string ] .

data:SortieEnd a ies:BoundingState ;
    ies:isEndOf data:Sortie20240717 ;
    ies:inPeriod [ a ies:ParticularPeriod ;
                   ies:iso8601PeriodRepresentation "2024-07-17T11:30:00Z"^^xsd:string ] .

# The aircraft actualising the Mach 2 disposition
data:FighterXYZ-123-Flying-20240717 a ex:FlyAtMach2 ;
    rdfs:comment "Fighter XYZ-123 flying at Mach 2 during Sortie 20240717"@en-GB ;
    ies:isParticipationOf data:FighterXYZ-123 ;
    ies:isParticipantIn data:Sortie20240717 .
```

## Summary

The disposition properties in IES provide a way to record what States *can* do — their potential — separately from what they *actually* do.

| Property | Pattern | Inference |
|---|---|---|
| `ies:hasDisposition` | State → ClassOfState (modal) | None — modal possibility only |
| `ies:eachHasDisposition` | ClassOfState → ClassOfState (modal) | None — modal possibility only |
| `ies:isDisposedTo` | Element → DispositionalClass | Entails `rdf:type` (existing pattern) |
| `ies:allHaveDisposition` | ClassOfElement → DispositionalClass | Entails `rdfs:subClassOf` (existing pattern) |

**Key principles:**

1. **Dispositions are modal** — a State can have a disposition without ever actualising it
2. **`hasDisposition` domain is `State`** — dispositions attach to temporal parts (or whole-life Entity instances, which are also States)
3. **Actualisation via `rdf:type`** — when a disposition is actually exercised, the State is typed as a member of the disposition's `ClassOfState`
4. **Conditional dispositions use conditional classes** — preconditions are encoded by defining a restricted `ClassOfState` and attaching `eachHasDisposition` to it
5. **`hasDisposition` and `eachHasDisposition` do not alter the type hierarchy** — the subject and the disposition target remain structurally separate

---

## Related Documentation

- [Instantiation Patterns](instantiation-patterns.md) — Standard patterns for creating IES data
- [4D Ontology Approach](4d-ontology.md) — Understanding States and temporal parts
- [Extending IES](extending-ies.md) — How to create domain-specific extensions

---

*© Crown Copyright 2020-2026*
