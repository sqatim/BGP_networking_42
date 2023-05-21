# Bgp At Doors of Autonomous Systems is Simple

## About

The purpose of this project is to expand your knowledge on BGP at the doors of autonomous systems. You will learn how to simulate a network and configure it using GNS3 with Docker images. This project involves using and installing Docker as well as GNS3. You will have to put all the configuration files of your project in folders located at the root of your repository. The folders of the mandatory part will be named [P1](/P1), [P2](/P2/), and [P3](/P3/). 

BGP EVPN is based on BGP (RFC 4271) and its extensions MP-BGP (RFC4760). BGP is the routing protocol that drives the Internet. Through MP-BGP extensions, it can be used to carry reachability information (NLRI) for various protocols (IPv4, IPv6, L3 VPN and in this case, EVPN). EVPN is a special family for publishing information about MAC addresses and the end devices that access them.

To complete this project, you will need to configure GNS3 with Docker images. This involves installing and configuring GNS3 as well as Docker in your virtual machine. You will also need to create two Docker images: one with a system of your choice containing at least Busybox or an equivalent solution, and another image using a system of your choice with specific constraints such as a software that manages packet routing (zebra or quagga), BGPD service active and configured, OSPFD service active and configured, an IS-IS routing engine service, and Busybox or an equivalent.

To complete this project, you will be undertaking three parts. Here are the descriptions for each part:

[Part 1](/P1): **Configuring GNS3 with Docker Images**

For the first part, your objective is to set up GNS3 with Docker images. This involves installing and configuring GNS3 as well as Docker within your virtual machine. Additionally, you will be required to create two Docker images. One image should contain a system of your choice, including at least Busybox or an equivalent solution. The other image should be built using a system of your choice, adhering to specific constraints such as having a software for packet routing management (zebra or quagga), an active and configured BGPD service, an active and configured OSPFD service, an IS-IS routing engine service, and Busybox or an equivalent.

[Part 2](/P2): **Configuring VXLAN Network with GNS3 and Docker**

In the second part, your focus shifts towards configuring a VXLAN (Virtual Extensible LAN) network using GNS3 and Docker. You will need to create two Linux-based virtual machines and configure them to establish communication over the VXLAN network. Additionally, you will be required to set up BGP EVPN (Border Gateway Protocol Ethernet VPN) on the virtual machines, enabling routing between them.

[Part 3](/P3): **Configuring BGP EVPN on a Network with GNS3 and Docker**

The third part revolves around configuring BGP EVPN on a network using GNS3 and Docker. Your task will be to design a network topology that incorporates multiple Linux-based virtual machines. These machines need to be configured with BGP EVPN. Furthermore, you will need to set up OSPF or IS-IS routing protocols on the virtual machines to facilitate routing between them.

## Subject

+ [Cloud-1 Subject](/BGP_subject.pdf)

## Key Terms:

1. **`BGP (Border Gateway Protocol)`**: BGP is the routing protocol that drives the Internet. It is used to exchange routing information between different autonomous systems (ASes) on the Internet.

2. **`MP-BGP (Multiprotocol BGP)`**: MP-BGP is an extension of BGP that allows it to carry reachability information for various protocols, including IPv4, IPv6, L3 VPN, and EVPN.

3. **`EVPN (Ethernet VPN)`**: EVPN is a special family for publishing information about MAC addresses and the end devices that access them. It is used in data center networks to provide Layer 2 and Layer 3 connectivity between servers and other devices.

4. **`VXLAN (Virtual Extensible LAN)`**: VXLAN is a network virtualization technology that allows you to create virtual networks over an existing physical network infrastructure.

5. **`GNS3`**: GNS3 is a network simulation software that allows you to simulate complex networks using virtual machines and other network devices.

6. **`Docker`**: Docker is a platform for developing, shipping, and running applications in containers. Containers are lightweight, portable environments that can run on any system with Docker installed.

7. **`Zebra and Quagga`**: Zebra and Quagga are open-source software packages that provide routing services for Unix-like operating systems.

8. **`Busybox`**: Busybox is a collection of Unix utilities designed for embedded systems with limited resources.
