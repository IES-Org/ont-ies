# What is a flow or stream?

A **Flow** or "stream" is a **State** that is the matter, energy or signal that crosses a surface or passes along path.

The term "flow" is a commonly used term in natural language, but "stream" is widely used in the process industry for flows of fluids within pipes. Where a **Flow** is of matter, the matter is continuously changing. This is analogous to the Eulerian view of a flow field -- see https://en.wikipedia.org/wiki/Lagrangian_and_Eulerian_specification_of_the_flow_field .

Consider the vehicles passing from junction 3 to junction 4 on the M4 is a **Flow**. **Vehicle** EK 09 LEF is part of this **Flow** between 12:00 and 12:15 on 2024-04-29. This is shown as a space-time diagram in Figure 1.

![Space-time diagram for a Flow of Vehicles](../../assets/images/diagrams/rendered/networks/Spacetime_diagram_for_a_Flow_of_Vehicles.jpg)

*Figure 1 - Space-time diagram for a Flow of Vehicles*

A record of the relationship between the **Flow** of vehicles and **Vehicle** EK 09 LEF is show Figure 2.

![Record of a Flow of Vehicles](../../assets/images/diagrams/rendered/networks/Record_of_a_Flow_of_Vehicles.jpg)

*Figure 2 -- Record of a Flow of Vehicles*

**Vehicle** EK 09 LEF travels from junction 3 to junction 4 as part of a **Movement** between London and Wales, as shown in Figure 3.

![Vehicle in a Movement](../../assets/images/diagrams/rendered/networks/Vehicle_in_a_Movement.jpg)

*Figure 3 - Vehicle in a movement*

A **Flow** can have physical properties. Useful physical properties for a **Flow** of vehicles include:

- total number of vehicles;
- number of vehicles per hour;
- number of vehicles per metre of road;
- average speed of vehicles.

Useful physical properties for a **Flow** of fluid include:

- total volume or mass;
- volume or mass flow rate;
- fluid density;
- average flow velocity.

## Connections between Flows

**Flows** can:

- be joined one to the next;
- merge or divide.

A **Flow** can be along a path or across a surface. A **Flow** across a surface can be a boundary at the start or finish of a **Flow** along a path.

The relationships between **Flows** can be recorded by **isPartOf** and the boundary relationships **isStartBoundaryOf** and **isFinishBoundaryOf**.

Consider the vehicles travelling westbound through M4 junction 4. At junction 4 there are four westbound **Flows**:

- vehicles arriving from junction 3 and continuing to junction 5;
- vehicles arriving from junction 3 and leaving the M4;
- vehicles joining the M4 and travelling to junction 5;
- vehicles leaving junction 4 and travelling to junction 5.

These flows are shown diagrammatically in Figure 4.

![Vehicles leaving and joining at a junction](../../assets/images/diagrams/rendered/networks/Vehicles_leaving_and_joining_at_a_junction.jpg)

*Figure 4 - Vehicles leaving and joining at a junction*

The relationships between the westbound arriving **Flows** and their boundaries are recorded as shown in Figure 5.

![Flows and boundaries](../../assets/images/diagrams/rendered/networks/Flow_and_boundaries.jpg)

*Figure 5 -- Flows and boundaries*

**Flows** can also be regarded as a **Network**. The equivalent to Figure 5 recorded as a Network is shown in Figure 6.

![Network of Flows](../../assets/images/diagrams/rendered/networks/Network_of_Flows.jpg)

*Figure 6 - Network of Flows*

## Flow and Event

In many cases, a **Flow** is output from one **Event** and input to another.

In the process industry, a process flow diagram (PFD) shows the **Flows** between **Events** ("unit operations" in process industry terminology). A typical PFD is shown in Figure 7.

![Typical PFD](../../assets/images/diagrams/rendered/networks/typical_pfd.png)

*Figure 7 - Typical PFD*

NOTE The symbols used for the **Events** are the same as those for the equipment items that perform them. Confusingly the **Events** shown on a PFD are also identified by the tags of the equipment items that will perform them.

A **Flow** can be a participant in an **Event**.

Figure 3 shown a single vehicle in motion as a participant in a **Movement Event**. Consider the **Flow** of vehicles from M4 junction 3 to junction 4 between 18:00 and 18:30 on Monday 2024-06-24. This **Flow** is a participant in the "Monday evening commute" **Event**, as shown in Figure 8.

![Flow participant in an Event](../../assets/images/diagrams/rendered/networks/Flow_participant_in_an_Event.jpg)

*Figure 8 -- Flow participant in an Event*

## Containment of Flow

A **Flow** of fluid can be contained by a pipe. A **Flow** of vehicles can be contained by a road.

Consider the **Flow** of vehicles from M4 junction 3 to M4 junction 4. Usually, this **Flow** is contained by the M4, but during the night of 2024-06-18 it is contained by the A4, Bath Road, because of road surfacing works. This is recorded as shown in Figure 9.

![Containment of a Flow of vehicles](../../assets/images/diagrams/rendered/networks/Containment_of_a_Flow.jpg)

*Figure 9 - Containment of a Flow of vehicles*

The **Containment** of a **Flow** can also be less precise, such as the energy **Flow** from electricity power stations to end consumers via the UK's electrical transmission and distribution networks.

EXAMPLE 1 The UK energy flows in 2022 are shown in Figure 10, taken from https://www.gov.uk/government/statistics/energy-flow-chart-2022 .

![UK energy flows in 2022](../../assets/images/diagrams/rendered/networks/Energy_Flow_Chart_2022_TWh.jpg)

*Figure 10 - UK energy flows in 2022*

In Figure 10, the red lines to the left of the "power stations" box represent electrical energy **Flows** through the UK electrical transmission and distribution networks. This is a kind of PFD, as shown in Figure 7. The box in the middle is labelled "power stations", but represents the energy conversion **Event** carried out by power stations.

## Flow at a location in a Network

Site 02 is on the B3322 which is part of the IoW road network. This can be recorded as shown in Figure 11.

![Location of a traffic monitoring site](../../assets/images/diagrams/rendered/networks/Location_of_a_traffic_monitoring_site.jpg)

*Figure 11 - Location of a traffic monitoring site*

Site 02 is not at a road junction, but placed between junctions. The subclass of **Node** "Free Flowing Traffic" indicates this.

> There is a semantic difficulty with Figure 11, because is merely an arbitrary boundary placed along the B3322, across which traffic passes. Therefore the **ies:isPartOf** relationship is correct.
>
> However an intermediate **Node** along a **Link** is not necessarily part of it. Therefore there is a choice: either regard an arbitrary boundary as something other than a **Node**, or as a special type of **Node**.
>
> Regarding the boundary site02 as a **Node** is convenient because B3322 can be split into two **Links** -- B3322 north of site 02, and B3322 south of site 02 -- each of which has site 02 as a **Node** at an end.

There are many relationships between **Flows** of traffic and a road **Network**. Consider the three statements:

- There is a northbound **Flow** of traffic along the B3322.
- The northbound **Flow** of traffic at site 02 is part of the northbound **Flow** of traffic along the B3322.
- The northbound **Flow** of traffic at site 02 between 2022-03-21T10:30 and 2022-03-21T10:45 is a **State** of the **Flow**, which is at a **State** of site 02.

These statements are shown in Figure 12.

![Containment of traffic monitored Flow](../../assets/images/diagrams/rendered/networks/Containment_of_traffic_monitored_flow.jpg)

*Figure 12 - Containment of traffic monitored Flow*

Figure 12 can be simplified, as follows:

- There is nothing to be said about the **Containment** objects in this example, and so they can be anonymous placeholders.
- Probably there is nothing to be said about the state of site 02 between 2022-03-21T10:30 and 2022-03-21T10:45. This would not be the case if site 02 was moving along the road.

Applying these simplifications gives Figure 13.

![Simplified containment of flows](../../assets/images/diagrams/rendered/networks/Simplified_Containment_of_traffic_monitored_Flow.jpg)

*Figure 13 - Simplified containment of flows*
