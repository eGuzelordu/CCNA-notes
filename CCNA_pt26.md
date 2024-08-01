# CCNA Part 26

## OSPF(Open Shortest Path First) Part 1

### Agenda:

* Basic OSPF Operations

* OSPF Areas

* Basic OSPF Configuration

#### Link state Routing Protocols

* Every router creates a 'connectivity map' of the network.

* Each router advertises information about its interfaces(connected networks) to its neighbors. These advertisements are passed along to other routers, until all routers in the network develop the same map network.

* Each router independently uses this map to calculate the best routes to each destination.


* Link state protocols use more CPU on the router however they react faster to changes in the network than distance vector protocols.

#### OSPF

* Uses the shortest path firs algorithm AKA dijkstras algo.

* Three Versions:

    * OSPFv1(1989): Old, not used anymore

    * OSPFv2(1998): Used for IPv4

    * OSPFv3(2008): Used for IPv6(also can be used for IPv4)

* Routers Store information about the network in LSAs(Link State Advertisements), which are organized in a structure called the LSDB(Link State Database).

* Routers will flood LSAs until all routers in the OSPF area develop the same map of the network(LSDB).

* In OSPF, there are three main steps in the process of sharing LSAs and determining the best route to each destination in the network.

    1) Become neighbors with other routers connected to the same segemnt.

    2) Exchange LSAs with neighbor routers.

    3) Calculate the best routes to each destination, and insert them into the routing table.

#### OSPF Areas

* OSPF uses areas to divide up network.

* Small networks can be single area without any negetive effects on the performance.

* In larger networks, a single area design can have negative effects:

    * The SPF algorithm algo takes more time than calculated.

    * The SPF algo requires exponentionally more processing power on the routers.

    * The larger LSDB takes up more memory on the routers.

    * Any small change in the network causes every router to flood LSAs and run the SPF algo again.

* The problems listed above can be solved by dividing up the network.

* Area 0 is called the BACKBONE area

* An area is a set of routers and links that share the same LSDB.

* The backbone area(area 0) is an area that all other areas must connect to.

* Routers wilth all interfaces in the same area they are called internal routers.

* Routers with interfaces in multiple areas are called Area Border Routers(ABR).

    * Area Border routers keep a seperate LSDB for each area they are connected to.

    * Max should be 2

    * Anything over 3 is considered overburn

* Routers connected to the backbone area (area 0) are called backbone routers.

* An Intra-Area Route is a route to a destination inside the same OSPF area.

* An inter-area route is a route to a destination in a diffrent OSPF area.

* OSPF Area Rules:

    * Areas should be Contigious(not divided up).

    * All OSPF areas must have atleast one ABR connected to the backbone area.

    * OSPF interfaces in the same subnet must be in the same area.

#### Basic OSPF Configuration

* `router ospf 'PROCESS ID'` - enter OSPF config mode.

* `network 'IP-ADDRESS' 'WILDCARD-SUBNET-MASK' 'AREA-NUM` - Activate OSPF on interfaces.

    * The `network` command tells OSPF:

        * Look for any interfaces with an IP address contained in the range specifies in the network command.

        * Activate OSPF on the interface in the specific area.

        * The rouetr will then try to become OSPF neighbors with OSPF-activated neighbor routers.

* `passive-interface INT` - Tells the router to stop sending OSPF 'hello' messages out of the interface.

    * The router will continue to send LSAs informing it's neighbors about the subnet config on the interface.

    * This command should be used on interfaces which dont have any OSPF neighbors.

* `ip route 0.0.0.0 0.0.0.0 'NEXT-HOP'` to configure a default route.

* `default-information originate` advertises the default route.

* `show ip protocol` - to see ip protocol.

* Router ID order of priority:

    1) Manual Configuration

    2) Highest Ip address on a loopback interface.

    3) Hishest IP address on a physical interface.

* `router-id A.B.C.D` - configure router id manualy.

* `clear ip ospf process` - resets ospf on the router.

* `maximum-paths ?` - changes the maximum amount of paths.

* `distance ?` - changes AD.
