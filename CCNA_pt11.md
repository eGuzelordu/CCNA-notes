# CCNA Part 11.1

## Routung Fundementals

## What is Routing?

* Is the proccess that routers use to determin the path that IP packets should take over a network to reach their destination.

    * Routers store routes to all of their known destinations in a routing table.

    * When routers receive packets, they look in the routing table to find the best route to forward that packet.

---
 
* There are two main routing methods to learn routes.

    * Dynamic routing: Routers use dynamic routing protocol(ie. OSPF) to share routing information with eachother automatically and build their route tables.

    * Static Routing: A network engineer/admin manually configures routes on the router.

---

* A route tells the router: To send a package to destination X you should send the Packet to the next-hop(the next router in the path to the destination) Y.

    * or, if the destination is directly connected to the router, send the packet directly to the destination.

    * or, if the destination is the router's own IP address, recieve the packet for yourself(dont forward it).

* WAN(Wide Area Network) a network that extends over a large geograpical area.

#### Pre-Configuring 

1) `interface 'port'`

2) `ip address 'ip-address' 'subnet-mask'`

3) `no shutdown`

* Do this for all ports

* `show ip route` - shows router routing table.

* A connected route is a route to the network the interface is connected to.

* A local route is a route to the exact IP address configured on the interface

# CCNA Part 11.2

## Static Routing

* To send packets to dewstiination outside their local network, they must send the packet to their default gateway.

* The default gateway config is also called a default route(gateway is another name for route).

    * It is a route to 0.0.0.0/0 = all netmask bits set to 0.

* End host usually have no need for any more specific routes.

    * They just need to know: to send packets outside of my local network, I should send them to my default gateway.

* Static routes are routes that are configured in so the routers know where to hop to inorder to get to the packet


### Configure static route

1) `ip route 'ip-address' 'subnet-mask' 'next-hop ip-address'`

2) do to every router.

EX. `ip route 192.168.1.0 255.255.255.0 192.168.34.3`

* `ip route ip-address netmask exit-interface`

* `ip route ip-address netmask exit-interface next-hop`

* Static routes in which you specify only exit interface rely on a feauture called Proxy ARP to function.

* this is usually not a problem, but generaly you can stick to `next-hop` or `exit-interface next-hop`.


### Configure Default route

* A default route is a route to 0.0.0.0/0

    * 0.0.0.0/0 is the least specific route possible; it includes every possible IP destination address.

* If the wouter doesn't have any more specific routes that match a packet's destination IP address, the router will forward the packet using the default route.

* A default route is often used to direct traffic to the internet.
    
    * More specific routes are used for destination in the internal corprate network.

    * Traffic to destination outside of the internal network is sent to the internet.

* to config default route use command

    * `ip route 0.0.0.0 0.0.0.0 next-hop`
