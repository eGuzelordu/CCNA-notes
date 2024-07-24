# CCNA Part 18

# VLANs Part 3

### Agenda

* Naitive VLAN on a router

* Layer 3 switching/Multilayer Switching

---

* The naitive VLANs benefit is that its more efficent due to it not having a tag.

* There are 2 methods of configuring the natice VLAN on a Router:

    * Use the command `encapsulation dot1q vlan-id naitive`

    * Configure the IP address for the naitive VLAN on the router's physical interface(the encapsulation dot1q vlan-id command is not necessary).

        * This is done by just configuring the interface as well as the subinterfaces the main interface will act as native VLAN

### Layer 3 Switches(Multi-Layer Switch)

* Capable of switching and routing.

* it is 'Layer 3 aware'

* You can assign IP addresses to its interfaces, like a router.

* You can create virtual interfaces for each VLAN and Assign IP Addresses to those interfaces.

* Your can configure routes on it, just like a router.

* It can be used for inter-VLAN routing.


### Inter-VLAN Routing vie SVI

* Switch Virtual Interfaces

    * SVIs are the virtual interfaces you can assign IP addresses to in a multilayer switch.

    * Configure each OC to use the SVI(Not the Router) as their gateway address.

    * To send traffic to different subnets/VLANs, the PCs will send traffic to the switch, and the switch will route the traffic.

    * in order to send packet out of the network establish a point to point subnet between the multilayer switch and the router then route things that dont match to the router via default route on the multilayer switch.
    
    * SVIs are shutdown by default.

    * SVI to be up/up on status and protocol

        * The VLAN must exist on the switch.

        * The switch must have atleast one access port in the VLAN in an up/up state, AND/OR one trunk port that allows the VLAN that is in up/up state

        * The VLAN must not be shutdown.

        * The SVI must not be shutdown.
