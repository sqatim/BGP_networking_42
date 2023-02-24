# Leaf 01 (Part 03)

```
ip link add br0 type bridge
ip link set dev br0 up
ip link add vxlan10 type vxlan id 10 dstport 4789
ip link set dev vxlan10 up
brctl addif br0 vxlan10
brctl addif br0 eth1

<!-- vtysh is a command-line interface (CLI) that provides a unified interface for configuring and managing network devices that use the Quagga routing software suite. Quagga is an open source routing software suite that implements various routing protocols, such as OSPF, BGP, RIP, and more, and vtysh is a part of this suite that allows users to configure and manage these protocols.

vtysh provides a single interface that allows users to configure and manage multiple routing protocols, rather than having to learn and use a separate interface for each protocol. This makes it easier for network administrators to manage complex networks with multiple routing protocols. -->

+ vtysh

<!-- conf t is a command that is commonly used in Cisco IOS-based networking devices to enter configuration mode. The full form of conf t is "configure terminal". When you enter conf t, you are taken to a special mode where you can modify the configuration of the device.

In configuration mode, you can configure various settings on the device, such as interface settings, routing protocols, access control lists (ACLs), and many others. The specific commands that are available in configuration mode depend on the device and the features that have been enabled on it. -->

conf t

hostname router_ouseqqam-2
no ipv6 forwarding
!
interface eth0
ip address 10.1.1.2/30
ip ospf area 0
!
interface lo
ip address 1.1.1.2/32
ip ospf area 0
!
router bgp 1
neighbor 1.1.1.1 remote-as 1
neighbor 1.1.1.1 update-source lo
!
address-family l2vpn evpn
neighbor 1.1.1.1 activate
advertise-all-vni
exit-address-family
!
router ospf
! 
```