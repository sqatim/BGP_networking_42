# PART 02

## VXLAN (Virtual Extensible LAN):

VXLAN is a network virtualization technologie that allows to create a virtual layer 2 network on top of a physical (underlay) IP network.
- The VXLAN overlay network is created by encapsulating layer 2 frames with VXLAN header that includes a 24-bit VNI (VXLAN Network Identifier) that acts as a segment ID to separate the virtual network from other virtual networks. The encapsulated frames are then sent over the underlay IP network, alowing hosts in different subnets to communicate with each other as if they were on the same physical network.
- The underlay network provides the transport mechanism  for the vxlan traffic and is responsible for forwording the encapsulated frames between VXLAN Tunnel End Points (VTEP), which are the devices that perfom the encapsulation and decapsulation of the VXLAN frames.

## VXLAN and spine-leaf architecture:
VXLAN can be used to impelement virtual networks in a spine-leaf architecture. The spine switches serve as the VXLAN routers, forwording the VXLAN packets between the leaf switches, while the leaf switches function as the endpoints for the virtual networks. this allows for the creation of multiple virtual L2 networks that are isoleted from each other, yet can share the same physical infrastructure.

![Figure](Spine-leaf.png)

## Address learning:
there are two ways to do this. One is learning through the data plane, and the other is learning through the control plane. but, before getting more details about these methodes, we need first to know about the types of traffic for communication: 
1. Types of traffic for communication (Unicast and BUM):

    - Unicast communication refers to a one-to-one communication where a single sender sends a message to a single recipient. In unicast communication, the sender knows the IP address or the MAC address of the recipient, and the message is delivered only to that specific recipient.

    - BUM (Broadcast, Unknown unicast, and Multicast) communication refers to a one-to-many communication where a single sender sends a message to multiple recipients. This type of communication includes three types of traffic:

        * Broadcast: A broadcast message is sent to all devices on a network. In this case, the sender does not know the specific IP or MAC address of the recipients, so it sends the message to a special broadcast address, such as 255.255.255.255, which is recognized by all devices on the network.

        * Unknown unicast: An unknown unicast message is sent to a single recipient, but the sender doesn't know the MAC address of the recipient. This typically occurs when a switch receives a unicast message for which it doesn't have a MAC address in its forwarding table. The switch then floods the message to all ports in the associated VLAN, in the hopes of locating the destination device.

        * Multicast: A multicast message is sent to a group of devices that have joined a multicast group. In this case, the sender sends the message to a multicast group address, such as 224.0.0.1, and the message is delivered only to the devices that have joined the group.

2. Data plane (Flood and Learn AKA Bridging):

    When a switch receives a packet on an input port, it first checks the destination MAC address of the packet to determine which output port the packet should be forwarded to. If the switch has not previously learned the MAC address of the destination device, it uses a technique called "flood and learn."
    In this technique, the switch floods the incoming packet to all of its output ports, except the input port that the packet was received on. By doing this, the switch ensures that the packet reaches the intended destination device, even if the switch does not yet know the destination device's MAC address.
    As the switch floods the packet, it also learns the source MAC address of the device that sent the packet, and associates that MAC address with the input port on which the packet was received. This allows the switch to update its MAC address table, which maps MAC addresses to input ports, and reduces unnecessary flooding of future packets with the same destination MAC address.
    Once the switch has learned the destination device's MAC address, it no longer needs to flood packets to all output ports. Instead, it forwards subsequent packets with the same destination MAC address directly to the output port associated with that MAC address in its MAC address table.

3. Control plane (EVPN BGP)

    EVPN BGP is a widely used control plane protocol for VxLAN networks that enables distributed learning of MAC addresses across the network. It is built on top of BGP, which is a well-known and widely used routing protocol. EVPN BGP uses BGP to exchange MAC and IP reachability information, which is then used to build a distributed forwarding table for VxLAN traffic. (for more details, read this [document](#)).
