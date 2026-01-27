# Location and Containment

## Introduction

This document discusses the relationship between the current relationship **inLocation** and the proposed extension to IES for containment. The document shows that the two approaches are consistent, but that containment has additional semantics.

## Batch of fluid in a tank example

Consider batch of fluid B-101 in tank T-101 on 2026-06-26. The space-time diagram for the batch of fluid being in the tank is shown in Figure 1.

![Batch of fluid in tank -- space-time diagram](../../assets/images/diagrams/rendered/networks/batch_fluid_spacetime.jpg)

*Figure 1 -- Batch of fluid in tank -- space-time diagram*

## Location of batch of fluid in a tank

During 2026-06-26, the batch B-101 is located in the interior of tank T-101. The instances are shown in Figure 2.

![Batch of fluid in tank -- location instances](../../assets/images/diagrams/rendered/networks/batch_fluid_location.jpg)

*Figure 2 -- Batch of fluid in tank -- location instances*

The corresponding TURTLE is as follows:

```turtle
:T-101-tank-and-interior a ndt:TankAndInterior .

:T-101-tank a ndt:Tank ;
    ies:isPartOf :T-101-tank-and-interior .

:T-101-tank-interior a ndt:TankInterior ;
    ies:isPartOf :T-101-tank-and-interior .

:T-101-tank-interior-on-2026-06-26
    ies:isStateOf :T-101-tank-interior .

:B-101-on-2026-06-26 ies:isStateOf :B-101 ;
    ies:inLocation :T-101-tank-interior-on-2026-06-26 .
```

## Containment of batch of fluid by a tank

During 2026-06-26, the batch B-101 is contained by tank T-101. The instances are shown in Figure 3.

![Batch of fluid in tank -- containment instances](../../assets/images/diagrams/rendered/networks/batch_fluid_containment.jpg)

*Figure 3 -- Batch of fluid in tank -- containment instances*

The corresponding TURTLE is as follows:

```turtle
:T-101-tank a ndt:Tank .

:T-101-tank-on-2026-06-26 ies:isStateOf :T-101-tank ;
    a ies:Container ;
    ies:isPartOf :B-101-in-T-101-on-2026-06-26 .

:B-101-on-2026-06-26 ies:isStateOf :B-101 ;
    a ies:Contained ;
    ies:isPartOf :B-101-in-T-101-on-2026-06-26 .

:B-101-in-T-101-on-2026-06-26 a ies:Containment .
```

## Conclusions

1. The **inLocation** and **Containment** approaches appear to say the same thing but the **Containment** approach has the additional semantics of constraining the **Contained** to remain within the **Container**. A neutrino can be part of the interior of a tank but is not constrained by the tank.

2. Identification of interior spaces is important, because a tank can contain more than one interior space. Similarly a building can have many interior spaces. The building Industry Foundation Classes (IFCs) has **IfcSpace** (see https://ifc43-docs.standards.buildingsmart.org/IFC/RELEASE/IFC4x3/HTML/lexical/IfcSpace.htm).

3. It is important to identify what is part of a tank and what is not. A level sensor is usually regarded as part of a tank, and therefore can be associated with a tank by an **inLocation** relationship. Similarly the heating, lighting and air-conditioning systems are usually regarded as part of a building, whereas furniture is inside a building without being part of it.
