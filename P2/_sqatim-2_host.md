# Multicast configuration (Host 02)

```
ip addr add 30.1.1.2/24 dev eth1
```

`ip addr add`: command is a Linux networking command used to add an IP address to a network interface.

    ip addr add <ip_address>/<subnet_mask> dev <interface_name>

    <ip_address>     :is the IP address to be assigned to the interface.
    <subnet_mask>    :is the subnet mask that defines the network portion of the IP address.
    <interface_name> : is the name of the interface to which the IP address should be assigned.