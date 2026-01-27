# Network

## What is a network?

A **Network** consists of one or more **Links** and **Nodes**.

A **Link** is an **Element** which is, or enables, a **Flow** between its ends. A **Link** can be, or enable, a **Flow** in either direction, or in just one direction. A **Link** can be an **Entity** such as a road, or an **Event** such as a distribution activity.

A **Node** is what exists at the end of a **Link**. A **Node** can be at the end of more than one **Link**. A **Node** is all or part of a **Connector** at the end of a **Link**, and can be a **Connection**.

> A **Network** consisting of **Links** and **Nodes** is a convenient way of presenting information which can be stated more precisely using **Connectors** and **Connections**.

The IES support for **Network** is shown as Figure 1.

![Network in IES](../../assets/images/diagrams/rendered/networks/Network_in_IES.jpg)

*Figure 1 - Network in IES*

NOTE 1 A **Network** can contain an assembly of **Links** which forms a **Loop** without an end. For simplicity, this has been omitted from the ontology, but could be added if a need arose.

NOTE 2 The relationships **hasStartEnd** and **hasFinishEnd** are used where a **Link** enables a **Flow** in only one direction. If required, **UniDirectionalLink** and **BiDirectionalLink** can be defined as subclasses of **Link**.

UK highways is a **Network**. A small part of the highway **Network** is shown in Figure 2.

![Part of a highway Network](../../assets/images/diagrams/rendered/networks/Part_of_a_highways_network.jpg)

*Figure 2 - Part of a highway Network*

A record of the Links L-1, L-2 and L-3, which have ends at N-7, is shown in Figure 3.

![Record of part of a highway Network](../../assets/images/diagrams/rendered/networks/Record_of_part_of_a_highways_network.jpg)

*Figure 3 - Record of part of a highway Network*

In Figure 3, it is assumed that a Highway Network is necessarily a **Network**, but that a Road is not necessarily a **Link** and that a Road Junction is not necessarily a **Node**.

## Networks that change with time

The **Links** that make up a **Network** can change with time. Consider **Network** X which changes each year as shown Figure 4.

![Changes to a Network](../../assets/images/diagrams/rendered/networks/Evolution_of_network.jpg)

*Figure 4 -- Changes to a Network*

The changes to the network are as follows:

- 2023: **Network** X consists of only **Link** A-B which has **Nodes** A and B at each end, with no intermediate **Nodes**.
- 2024: **Network** X consists of only **Link A-B**, which now has intermediate **Node** C. **Link** A-B, now consists of **Link** A-C and **Link** C-B.
- 2025: **Network** X consists of **Link** A-B and **Link** C-D.

A record of the changes to the network using IES is shown in Figure 5.

![Record of changes to a network](../../assets/images/diagrams/rendered/networks/Record_of_evolution_of_network.jpg)

*Figure 5 - Record of changes to a network*

## Networks with levels of detail

A **Network** can be described at different levels of detail. For example, a **Link** can be decomposable into several parallel **Links**. Similarly a **Node** can be decomposable into several **Nodes** with internal **Links** between them.

A **Link** can be decomposed in two ways:

> **parallel**: A parallel part has the same end **Nodes** as the whole, such that a **Flow** through the whole can but need not pass through the part.
>
> **series**: A series part has **Nodes** which are at the ends of the whole or within the whole, such that each **Flow** through the whole passes through the part.

Consider **Network** X which can be described at different levels of detail as shown in Figure 6.

![Levels of detail of a Network](../../assets/images/diagrams/rendered/networks/Levels_of_detail_for_a_network.jpg)

*Figure 6 -- Levels of detail of a Network*

The levels of detail in the description of **Link** A-B in **Network** X are as follows:

- level 1: **Link** from A to B.
- level 2: **Link** from A to B, with an intermediate **Node** at C. The intermediate **Node** was considered insignificant at level 1.
- level 3: The **Link** from C to B is decomposed into two parallel **Links**.
- level 4: **Node** C is decomposed into three interconnected **Nodes**.

The semantics of the increasing detail between level 3 and level 4 is complicated. Consider the **Link** A-C:

- At level 3, the **Nodes** A and C are the ends of the **Link** A-C. **Node** C is also an end of **Links** C-B/1 and C-B/2,
- At level 4, the **Nodes** A and C/3 are ends of **Link** A-C/a. But Node C/3 is not an end of **Links** C-B/1a and C-B/2a. Instead the **Connections** require **Links** C/1-3 and C/2-3.

> Therefore **Link** A-C/a is a series part of **Link** A-C but not all of it.

## Connection between Networks

Two different **Networks** can be connected. The connection can be at a **Node**, or via a **Link**, and recorded with different levels of detail, as shown in Figure 7.

![Connection between networks](../../assets/images/diagrams/rendered/networks/Border_between_networks.jpg)

*Figure 7 - Connection between networks*

The **Elements** that are part of both **Networks** for the different approaches are as follows:

**border Node**: The **Node** identified as B or P is end of **Link** A-P, **Link** P-Q and **Link** P-R. It is also part of **Network** X and **Network** Y.

**border Link**: The **Link** B-P is part of **Network** X and **Network** Y.

**border Node or Link**: The **Node** identified as B or P is end of **Link** A-P, **Link** P-Q and **Link** P-R. It is also part of **Network** X and **Network** Y. The **Link** B/X-P/Y is also part of **Network** X and **Network** Y.

## Scope of a route or path

What is included within a **Link** or **Node** is a choice and is defined by its subclass.

EXAMPLE 1 The "OS road" subclass of **Link** includes just the paved surface and the void above it through which vehicles can travel.

EXAMPLE 2 The "National Highways road" subclass of **Link** includes all of an "OS road", and also the footways and verges.

EXAMPLE 3 A "Railway line" subclass of **Link** can be defined to include the track, embankments, cuttings, bridges and all civil structure necessary for the railway, along with the signalling equipment and the and the "railway operating centres" (signal boxes).

EXAMPLE 4 A "Railway station" subclass of **Node** can be defined to include platforms, foot bridge, ticket office, and waiting room.

## Network in IES and EU INSPIRE

### The INSPIRE network model

The overview of the EU's INSPIRE Directive states:

> INSPIRE Directive aims to create a European Union Spatial Data Infrastructure (SDI) for the purposes of EU environmental policies and policies or activities which may have an impact on the environment. This European Spatial Data Infrastructure will enable the sharing of environmental spatial information among public sector organisations, facilitate public access to spatial information across Europe and assist in policy-making across boundaries.

The complete text of the overview can be found at https://knowledge-base.inspire.ec.europa.eu/overview_en.

The INSPIRE network model is defined in the Generic Network Model.

The INSPIRE network model is for a network at a single instant in time and has no support for time-varying networks. This limitation is addressed by the IES, which represents an individual at different times by states.

### Mapping between INSPIRE and IES

| INSPIRE class | IES class | Relationship between INSPIRE and IES |
|---------------|-----------|--------------------------------------|
| **network** | **Network** | The classes are identical, except that an IES **Network** can be divided into part **Networks**. Hence a single INSPIRE **generalised link** can also be an IES **Network**. |
| **generalised link** | **Link** | The classes are identical, except that an IES **Link** can lose or gain intermediate **Nodes** over time. |
| **link** | **Link** | An IES **Link** is more general than an INSPIRE **link**, because it can have intermediate **Nodes**. The intermediate **Nodes** may only be of interest at some levels of detail |
| **directed link** | **Link** | In IES, directionality can be assigned to any **Link** by specifying start and finish ends. |
| **link sequence** | **Link** | An IES **Link** can have intermediate **Nodes**. The intermediate **Nodes** may only be of interest at some levels of detail. |
| **node** | **Node** | The classes are identical, except that an IES **Node** can have parts **Nodes** and **Links** at some levels of detail. |
| **link set** | **Network** | In IES, a part of a **Network** consisting of one or more **Links** is another **Network**. |
| **network connection** | n/a | Nothing explicit is required for a connection between **Networks** in IES. A **Node** or **Link** can be part of more than one network. |
| **network element** | n/a | This is an IT "abstract supertype", which has no role within an ontology. |

## Network and connections

A **Network** provides a high-level view which does not show the details of how **Links** are connected to **Nodes**. A **Network** definition and a detailed definition using instances of **Connection** can both exist within the same dataset.

Consider the road junction shown in Figure 9.

![Road junction](../../assets/images/diagrams/rendered/networks/Road_junction.jpg)

*Figure 9 - Road junction*

This view relies upon a record of the three **Connections**:

- through **Connection** between the Tee junction and A3055 north of the junction;
- through **Connection** between the Tee junction and A3055 south of the junction;
- joining **Connection** between the Tee junction and B3399 east of the junction.

The record is shown as UML in Figure 10.

![Record of road junction connections](../../assets/images/diagrams/rendered/networks/Record_of_road_junction_connections.jpg)

*Figure 10 - Record of road junction connections*

In Figure 10, each Connection is classified. A **Network** view of the same road junction is shown in Figure 11.

![Network view of a road junction](../../assets/images/diagrams/rendered/networks/Network_view_of_a_road_junction.jpg)

*Figure 11 - Network view of a road junction*

Figure 11 does not record the **Connections**, but merely shows that **Flows** are possible along the A3055 and between B3399 and the A3055. A record of the **Network** view is shown in Figure 12.

![Record of a network view of a road junction](../../assets/images/diagrams/rendered/networks/Record_of_a_network_view_of_a_road_junction.jpg)

*Figure 12 - Record of a network view of a road junction*

Figure 12 is much simpler than Figure 10, but has less information. It is not explicit that the A3055 is straight on through the junction, but B3399 joins.

## Routing

### Graph with weights

A graph is a set of vertices and a set of edges, each of which has a vertex at each end. The edges can be directed so that one vertex is the start and the other the finish.

Routing algorithms have a graph as input, with weights that are assigned to each edge. The weights can be physical route distances, travel times, or costs. A routing algorithm finds the path between two vertices in a graph for which the sum of the weights is a minimum.

NOTE 2 Some definitions of a graph do not allow two different links between the same pair of nodes. This is called "multiple adjacency". This is no problem for a routing algorithm because the link with the higher weight can be ignored.

### Graph and network

A graph is a mathematical object, analogous to set, and not something physical. A **Network** is a physical individual (**ies:Element**). Being a **Node** or a **Link** is a role within a **Network**. A **Network** can be represented by a graph, where **Nodes** are represented by vertices and **Links** are represented by edges.

NOTE The GraphML schema uses the term "node" rather than "vertex".

A **Network** has states, and can contain different **Nodes** and **Links** in different states.

A **Network** has multiple levels of detail. A **Node** can have other **Nodes** and **Links** between them as parts. A **Link** can have other **Links** as parallel parts between the same pair of **Nodes**. A **Link** can have other **Links** as series parts along its length and intermediate **Nodes**.

A graph can be a representation of a **Network** for a particular state at a particular level of detail. A graph is can be an interface between a record of a Network and a routing application, as shown in Figure 13.

![Network, graph and routing application](../../assets/images/diagrams/rendered/networks/network_graph_and_application.jpg)

*Figure 13 - Network, graph and routing application*

### Extracting a graph from a source

Many of the highways data sources are graphs with some additional data. In these cases, extracting a graph to support routing applications is straightforward. IES is more difficult because it supports different levels of detail. A single level of detail has to be extracted to support routing. The is shown by the example in Figure 14.

![Two levels of detail](../../assets/images/diagrams/rendered/networks/two_levels_of_detail.jpg)

*Figure 14 - Two levels of detail*

In Figure 14, link A is decomposed into two links A-1 and A-2 for a purpose unrelated to routing, such as highway maintenance. A record of the links according to IES is shown in Figure 15.

![Record of levels of detail](../../assets/images/diagrams/rendered/networks/record_of_levels_of_detail.jpg)

*Figure 15 - Record of levels of detail*

If a graph is extracted, relying only upon the **hasEnd** relationships between **Links** and **Nodes**, then the graph shown in Figure 16 will be obtained.

![Incorrect graph](../../assets/images/diagrams/rendered/networks/incorrect_graph.jpg)

*Figure 16 - Incorrect graph*

Figure 16 shows a graph which will give incorrect answers when processed by a routing application. A routing application would assume that if **Link** A is blocked, then an alternative route is available via **Links** A-1 and A-2.

### Separating routing data from other IES data

Possibly a sufficiently clever algorithm can process whole part relationships, and extract a graph with a chosen level of detail. However, it may be better not to create the problem in the first place.

The triples to be used for routing can be held as a separate data base. A record of the division of **Links** into parts, or of the amalgamation of **Links**, for purposes other than routing can be held elsewhere, as shown in Figure 17.

![Separate routing data](../../assets/images/diagrams/rendered/networks/separate_routing_data.jpg)

*Figure 17 - Separate routing data*
