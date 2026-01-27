# Containment

An **Element** can contain one or more other **Elements**. An **Element** that contains, or is intended to contain, is a **Container**. An **Element** that is contained is a **Contained.**

A **Containment** is an **Element** that has as parts:

- a single instance of **Container**;
- one or more instances of **Contained**.

A **Containment** has states, and has properties which can change through time. For example a **Containment** can become leaky.

The classes **Containment**, **Container** and **Contained** are subclasses of **Element** and not **State** because a member of any can be an **Event**. For example, a flock of sheep can be contained by an **Event** that is a circling sheepdog. Also an **Event** that is a reaction can be contained by a vessel.

EXAMPLE The loaded pallet L-101 is contained in the shipping container PS-101 during delivery D-101. The shipping container PS-101, with loaded pallet-101 inside, is loaded on to ship MV Huge on passage P-101.

The **Containment** of the loaded pallet in the shipping container during delivery D-101 is shown in Figure 1.

![Containment of loaded pallet in shipping container](../../assets/images/diagrams/rendered/networks/containment_of_loaded_pallet_in_shipping_container.jpg)

*Figure 1 - Containment of loaded pallet in shipping container*

The **Containment** of the shipping container and its contents in the ship on passage P-101 is shown in Figure 2.

![Containment of shipping container and contents in ship](../../assets/images/diagrams/rendered/networks/containment_of_shipping_container_and_contents_in_ship.jpg)

*Figure 2 - Containment of shipping container and contents in ship*
