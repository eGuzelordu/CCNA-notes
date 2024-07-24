# CCNA Part 20

## STP(Spanning Tree Protocol)

### Agenda

* Redundancy in networks

* STP

#### Network Redundancy

* Redundancy is an essential part of network design.

* If one network component fails, you must ensure that other components will take over with little or no downtime.

* As much as possible, you must implememnt redundancy at every possible point.

---

* Without spanning tree the loops in the network could get out of control.

* Broadcast storm - when enough of these looped broadcasts accumulated in the network the network will be too congested for legitimate traffic to use the network. 

* MAC Address Flapping - switches continously updating their MAC address table.


#### Spanning Tree Protocol:

* Classic Spanning Tree Protocol is IEEE 802.1D.

* Switches from ALL vendors run STP by default.

* STP prevents layer 2 loops by placing redundant ports in a blocking state, essentially disabling the interface.

* These interfaces act as backuos that can enter a forwarding state if an active(= current forwarding) interface fails.

* Interfaces in a forwarding state behave normally. They send and recieve all normal traffic.

* Interfaces in a blocking state only send or recieve STP messages (Called BPDUs = Bridge Protocol Data Units).

* spanning tree protocol uses the term bridge instead of switches.

* By selecting which ports are forwarding and which ports are blocking, STP Creates a single path to/from each point in the network. This Prevents Later 2 Loops.

* There is a set process that STP uses to determine which ports should be forwarding and which be blocking.

* STP-enabled switches send/recieve Hello BPDUs out of all interfaces the default timer is 2 seconds(The switch will send a Hello BPDU out of every interface, once every 2 seconds).

* If a switch recieves a Hello BPDU on an interface, it knows that interface is connected to another switch(routers, PCs, etc. do not use STP, so they do not send Hello BPDUs).

* Switches use one field in the STP BPDU, the Bridge IP field, to elect a root bridge for network.

* The switch with the lowest Bridge ID becomes the root bridge.

* All ports on the root bridge are put in a forwarding state, and other switches in the topology must have a path to reach the root bridge.

* Original Bridge ID consists of 2 parts

    * Bridge Priority

        * 2 bytes

        * The default bridge priority is 32768 on all witches, so by defaukt the MAC address is used as the tie Breaker(Lowest MAC address becomes the root bridge).

        * The bridge Priority is compared first. if they tie, the MAC address is then compared.

    * MAC Address

* Modern Bridge ID divides the bridge priority into two subsections.

    * Bridge Priority.

        * 4 bits in length.

    * Extended System ID(= VLAN ID)

        * 12 bits in length.

        * Cisco switches use a version of STP called PVST(Per-VLAN Spanning Tree). PVST runs a separate STP 'instance' in each VLAN, So in each VLAN diffrent interfaces can be forwarding/blocking.

* When a switch is powered on it assumes it is the root bridge.

* It will only give up its position if it recevies a 'superior' BPDU(lower bridge ID)

* Once the topology has converged and all switches agree on the root bridge, only the root bridge sends BPDUs.

* Other switches in the network will forward these BPDUs, but will not generate their own original BPDUs.

#### STP steps:

1) One switch is elected as the root bridge. All ports on the root bridge are designated ports(forwarding state).

    * Root Bridge Selection:

        1) Lowest Bridge ID

2) Each remaining switch will select ONE of its interfaces to be its root port(Forwarding state). Ports across the root port are always designated ports.

    * Root Poert Selection:

        1) Lowest root cost

        2) Lowest neighbor bridge ID

        3) Lowest neighbor Port ID

3) Each remaining collision domain will select ONE interface to be a designated port(forwarding state). The other ports in the collision domain will be non-designated(blocking)

    * Designated port Selection

        1) Interface on switch with lowest root cost.

        2) Interface on switch with lowest bridge ID.


#### STP Cost Table

|Speed|STP Cost|
|---|---|
|10 Mbps|100|
|100 Mbps|19|
|1 Gbps|4|
|10 Gbps|2|

* The cost only matters on the sending interface.


