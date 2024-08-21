# CCNA Part 33

## IPv6 Part 3

### Agenda:

* IPv6 header

* Neighbor Discovery Protocol(NDP)

* SLAAC

* IPv6 static routing.

### IPv6 Header

* IPv6 header is a fixed length of 40 bytes.

* Version: 4 bits. indicates version of IP

* Traffic class: 8 bits. used for QoS to indicate high-priority traffic

* Flow Label: 20 bits. Used to identify specific traffic flow

* Length: 16 bits. Indicatess the length of the payload.

* Next header: 8 bits. indicates the type of the Next header.

* Hop Limit: The value in this field is descremented by 1 by each router that forwards it. If it reaches 0, the packet is discarded.

* Source/Destination address: 128 bits each. source and destination IPv6 addresses.

### Solicited-Node Multicast Address

* An IPv6 solicited-node multicast address is calculated from a unicast address.

* `ff02::1:ff` + Last 6 digits of the unicast address.

* Ex. 

```
x = 2001:0db8:0000:0001:0f2a:4fff:fea3:00b1

getLast 6 hex (x) -> a3:00b1

concat to ff02::1:ff -> ff02::1:ffa3:b1 

```

### Neighbor Discovery Protocol(NDP)

* Is a protocol used in IPv6.

* Replaces ARP

* The ARP like function of NDP uses ICMPv6 and solicited-node multicast addresses to learn the MAC address of other hosts.

* Two types of messages are used:

    * Neighbor Solicitation (NS) = ICMPv6 Type 135

    * Neighbor Advertisement (NA) = ICMPv6 Type 136

* Neighbor Solicitation (NS):

    * instead of using brodacast it uses multicast.


* Another function of NDP allows hosts to automatically discover routers on the local network.

* Two messeges used for this process:

    * Router Solicitation(RS) = ICMPv6 type 133

        * Sent to dulticast `ff02::2`(all routers).

        * Asks all routers on the local link to identify themselves.

        * Sent when an interface is enabled/host is connected to the network.

    * Router Advertisement(RA) = ICMPv6 Type 134

        * Sent to multicast address `ff02::1` (all nodes).

        * The router announces its presence, as well as other info about the link.

        * These messages are sent in response to RS messages.

        * They are also sent periodically, even if the router hasn't recieved an RS.

### SLAAC

* Stands for Stateless Address Auto-config.

* Hosts use the RS/RA messages to learn the IPv6 prefix of the local link and then automatically generate an IPv6 address.

* Using the `ipv6 address *prefix/prefix-length* eui-64` command, you need to manually enter the prefix.

* Using the `ipv6 address autoconfig` command, you dont need to enter the prefix. The device uses NDP to learn the prefix on the local link.

* The device will use EUI-64 to generate the interface ID, or it will be randomly generated

### DAD

* Duplicate address detection.

* Allows hosts to check if other devices on the local link are using the same IPv6 address.

* anytime an IPv6-enabled interface initializes(`no shutdown` command), or aand IPv6 address is configured on an interface(by any method:manual, SLAAC, etc.), it performs DAD.

* DAD uses two messages: NS and NA.

* The host will send an NS to its own IPv6 address. If it doesn't get a reply, it knows the address is unique.

* If it gets a reply, it means another host on the network is already using the address.

### IPv6 Static Routing

* IPv6 routing works the same as IPv4

* The routing tables and the processes are diffrent.

* IPv6 must be enabled by using `ipv6 unicast-routing` command.

