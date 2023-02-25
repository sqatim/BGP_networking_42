# Multicast configuration

## Router 1

```
ip link add br0 type bridge
ip link set dev br0 up
ip addr add 10.1.1.1/24 dev eth0
ip link add name vxlan10 type vxlan id 10 dev eth0 group 239.1.1.1 dstport 4789
ip addr add 20.1.1.1/24 dev vxlan10
brctl addif br0 eth1
brctl addif br0 vxlan10
ip link set dev vxlan10 up
```

## Router 2

```
ip link add br0 type bridge
ip link set dev br0 up
ip addr add 10.1.1.2/24 dev eth0
ip link add name vxlan10 type vxlan id 10 dev eth0 group 239.1.1.1 dstport 4789
ip addr add 20.1.1.2/24 dev vxlan10
ip link set dev vxlan10 up
brctl addif br0 eth1
brctl addif br0 vxlan10
```

## Hostname 1

```
ip addr add 30.1.1.1/24 dev eth1
```

## Hostname 2

```
ip addr add 30.1.1.2/24 dev eth1
```

---

## Configuration explanation:

`ip link`: command in linux used to show information about network interfaces and to performs various operations on newtork interfaces.

`ip link add`: command used to add a new network interface (or link) to a system. This command creates a new interface and sets its initial configuration.

    ip link add dev <name> type <type> [options]

    <name>    : is the name of the new interface to be created.
    <type>    : specifies the type of the new interface, which can be one of several types such as ethernet for wired interfaces, wifi for wireless interfaces, bridge for network bridge interfaces, etc.
    [options] : are additional options that can be used to specify the initial configuration of the new interface, such as the MAC address, MTU (maximum transmission unit), VLAN (virtual LAN) tag, and more.


`ip link add name vxlan10 type vxlan id 10 dev eth0 group 239.1.1.1 dstport 4789`: this command creates a new VXLAN interface.

    + name vxlan 10  : specifies the name of the new interface, in this case <vxlan10>.
    + type vxlan      : specifies the type of interface being created, in this case a vxlan interface.
    + id 10           : option specifies the vxlan identifier (VNI). which is used to distinguish between different VXLAN segment on the network.
    + dev eth0        : option specifies the physical ethernet interface that the VXLAN interface will use as its underlaying transport.
    + group 239.1.1.1 : this sets the multicast group used for the VXLAN traffic to 239.1.1.1, which means that all hosts in the same multicast group will receive the traffic.
    + dstport 4789    : option specifies the destination port used by the VXLAN, which is the port that the VXLAN traffic will be sent to on the remote endpoint. this option is used to soecify the default valuue for the VXLAN destination, wich is 4789.

`ip link set dev`: command is a Linux networking command used to modify the state of a network interface, such as bringing it up or down.

    + ip link set dev <name> up   : this command bring <name> interface up, meaning that the interface is enabled and can be used to send and receive network traffic.

    + ip link set dev <name> down : This command will disable the <name >interface and prevent it from sending or receiving network traffic.

`ip addr add`: command is a Linux networking command used to add an IP address to a network interface.

    ip addr add <ip_address>/<subnet_mask> dev <interface_name>

    <ip_address>     :is the IP address to be assigned to the interface.
    <subnet_mask>    :is the subnet mask that defines the network portion of the IP address.
    <interface_name> : is the name of the interface to which the IP address should be assigned.

`brctl addif`: The `brctl` command is a Linux networking command used to manage network bridges. A network bridge is a virtual network device that connects multiple network interfaces together, allowing them to communicate with each other as if they were connected to the same physical network. The `brctl addif` used to add a network interface to an existing bridge.

    brctl addif <bridge_name> <interface_name>

    <bridge_name>    :is the name of the bridge to which the interface should be added.
    <interface_name> :is the name of the interface that should be added to the bridge.