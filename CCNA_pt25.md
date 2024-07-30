# CCNA Part 25

## RIP & EIGRP

### Agenda

* Routing information Protocol(RIP)

* Enhanced Interior Gateway Routing Protocol(EIGRP)

#### RIP

* Routing Information Protocol(Industry standart).

* Distance vector IGP(Uses routing-by-rumor logic to learn/share routes)

* Uses hop count as its metric. One router = one hop(bandwidth is irrelevant)

* The maximum hop count is 15(anything more is considered unreachable)

* Has 3 versions:

    * RIPv1 and RIPv2 used for IPv4

    * RIPng(RIP Next Generation), used for IPv6

* Uses two message types:

    * Request: To ask RIP-enabled neighbor routers to send their routing table.

    * Response: To send the local routers routing table to neigboring routers.

* By default, RIP-enabled routers will share their routing table every 30 sec.

    * This can cause problems in big networks as these regular updates can clogg up the networks.

* RIPv1:

    * Only advertises classful addresses

    * doesnt support VLSM, CIDR

    * Doesn't include subnet mask information in advertisements(Response messages).

    * Masseges are broadcast to 255.255.255.255

* RIPv2:

    * Support VLSM and CIDR

    * Includes subnet mask information in advertisments

    * messages are multicast to 244.0.0.9

* Broadcast messages are delivered to all devices on the local network.

* messages are delivered only to devices that have joined that specific multicast group.

* inorder to config router follow the commands:

    * `router rip`

    * `version num`

    * `no auto-summary`

    * `network ip-address`

        * The network command tells the router to:

            * Look for interfaces with an IP address that is in the specified range

            * Active RIP on the interface that fall in the range

            * From adjacencies with connected RIP neighbors.

            * Adverise the network prefix of the interface.

        * The OSPF and EIGRP network commands oparate in the same way.
    
    * `passive-interface int`

        * The passive-interface command tells the router to stop sending RIP advertisemnets out of the specified interface

        * However the router will continue to adverise network prefix of the interface to its RIP neighbors.

        * You should alwyas use this command on interfaces that dont have RIP neighbors.

    * `show ip interface`

#### EIGRP

* Enhanced Interior Gateway Protocol

* Was Cisco proprietary, but Cisco has now published it openly so other vendors can implement it on their equipment.

* Musch faster than RIP in reacting to changes in the network.

* Does not have the 15 'hop-count' limit of RIP

* Sends messages using multicast address 224.0.0.10

* Is the only IGP that can perfom unequal-cost load-balancing(by default it performs ECMP load-balancing over 4 paths like RIP).

* for configuring EIGRP the only diffrence it the first command is `router eigrp 1`

* When configuring network it uses a wildcard mask:

    * A wildcard mask is basically an 'inverted' subnet mask.

    * 255.255.255.0 would be 0.0.0.255

#### SIDE notes:

* The network command doesnt tell the router which networks to advertise. it tells the router which interfaces to activate RIP on, and then the router will advertize the network prefix.
