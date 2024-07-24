# CCNA Part 21

## STP Part 2

### Agenda:

* STP states/timer

* STP BPDU

* STP optinal features

* STP configs

#### Spanning Tree Port States

|STP Port State|Stable/Transitional|
|---|---|
|Blocking|Stable|
|Listening|Transitional|
|Learning|Transitional|
|Forwarding|Stable|
|Disabled|admin shut down|

* Root/Designated ports remain stable in a Forwarding state.

* Non-designated ports remain stable in a Blocking state.

* Listening and learning are transitional states which are passed through when an interface is activated, or when a Bloacking port must reansition to a Forwarding state due to a change in the network topology.

#### Blocking State

* Non-designated ports are in a blocking state.

* Interfaces in a blocking state are effectively disabled to prevent loops.

* Interfaces in a blocking state do not send/recieve regular network traffic.

* Interfaces in a blocking state receive STP BPDUs.

* Interfaces in a blocking state do not forward STP BPDUs.

* Interfaces in a blocking state do not learn MAC addresses.

#### Listening State

* After the blocking state, interfaces with designated or root role enter the listening state.

* Only Designated or root ports enter the listening state(Non-designated ports are always blocking).

* The Listening state is 15 seconds long by default. this is determined by the Forward delay timer.

* An Interface in the listening state only forwards and recieves STP BPDUs.

* An interface in the Listening state doesn not send or recieve regular traffic.

* An interface in the Listening state does not learn MAC addresses from regular traffic that arrives on the interface.

#### Learning State

* After Listening state, a designated or roote port will enter the Learning state.

* The Learning state 15 seconds long by default. This is determined by the Forward delay timer(the same timer is used for both the listening and learning states).

* An interface in the learning state ONLY sends and recieves STP BPDUs.

* An interface in the learning state does not send or recieve regular traffic.

* An interface in the learning state learns MAC addresses from regular traffic that arrives on the interface.

#### Forwarding State

* Root and designated ports are in a forwarding state.

* A port in the forwarding state oparate as normal.

* A port in the forwarding state sends and recieves BPDUs.

* A port in the forwarding state sends and recieves normal traffic.

* A port in the forwarding state learns MAC addresses.

#### STP States:

|STP Port State|Send/Receive BPDUs|Frame Forwarding(regular traffic)|MAC Address Learning|Stable/Transitional|
|---|---|---|---|---|
|Blocking|No/Yes|No|No|Stable|
|Listening|Yes/Yes|No|No|Transitional|
|Learning|Yes/Yes|No|Yes|Transitional|
|Forwarding|Yes/Yes|Yes|Yes|Stable|
|Disabled|No/No|No|No|Stable|

#### Spanning Tree Timers:

|STP Timer|Purpose|Duration|
|---|---|---|
|Hello|How often the root bridge send hello BPDUs|2 sec|
|Forward Delay|How long the switch will stay in the Listening and learning states(each 15 second = total of 30)|15 sec|
|Max Age|How long an interface will wait after ceasing to receive Hello BDPUs to change the STP topology|20 sec (10 * hello)|

* Switches will only send/forward hello BPDUs on their designated ports

#### Max Age Timer

* Waits 20 seconds to see if a failure occured in the network.

* If another BPDU is recieve before the MAX age timer counts down to 0, the time will reset to 20 sec

* If another BPDU is not received, the max age timer counts down to 0 and the switch will reevaluate its STP choices, including root bridge, and local root, designated, and non-designated ports.

* If a non-designated port is selected to become a designated or root port it will transition from the blocking state to the listening state(15 sec), learning state(15 sec), and then finally the forwarding state. So it can take a total of 50 sec for a blocking interface to transition to forwarding.

* These timers and transitional states are to make sure that loops arent accidentlly created by an interface moving to forwarding state too soon.

---

* The Destination for BPDU is: `PVST+ (01:00:0c:cc:cc:cd)` 

* PVST only supports Ciscos ISL trunk encapsulation.

* PVST+ supports 802.1Q.

* Regular STP(not Cisco PVST+) uses a destination MAC address of `0180.c200.0000`

#### Spanning Tree Optional Features(STP toolkit)

* Portfast:

    * Enabled on interfaces that are connected to end hosts.

    * Makes it so that end hosts dont have to Listening and Learning states.

    * Allows a port to move immediatley to the Forwarding state, bypassing Listening and Learning.

    * If used, it must be enabled only on ports connected to end hosts.

    * If enabled on a port connected to another switch it could cause a layer 2 loop.

    * Its activivated by `spanning-tree portfest` won't enable it on a trunk port.

    * `spanning-tree portfest default` this enables portfast in all access ports.

    * Its dangerous. it can cause loops if things get switched around.

* BPDU Guard:

    * If an interface with BPDU Guard enabled receives a BPDU from another switch, the interface will be shot down to prevent a loop from forming.

    * `spanning-tree bpduguard enable` to enable

    * `spanning-tree portfast bpduguard default` to allow on all interfaces.

    * to enable a port that was enabled by a BPDU guard follow commands `shutdown` followed by `no shutdown`

        * if the problem isnt solved it will shut it down again.

* Root Guard:

    * If you enable root guard on an interface, even if it recieves a superior BPDU(lower bridge IP) on that interface, the switch will not accept the new switch as the root bridge. The interface will be disabled.

* Loop Guard:

    * If you enable loop guard on an interface, even if the interface stops receiving BPDUs, it will not start forwarding. The interface will be disabled.

#### Basic spanning tree configs:

* `spanning-tree mode mst`: Multiple spanning tree mode

* `spanning-tree mode pvst`: Per-VLAN spanning tree mode

    * Classic spanning tree

* `spanning-tree mode rapid-pvst`: Per-VLAN rapid spanning tree mode

    * Improved classic spanning tree.

    * industry standart.

* `spanning-tree vlan 1 priority 'Brige-ID'` or `spanning-tree vlan 'vlan num' root primary/secondary` is how you change the root bridge.

* configure cost and priority.

    * `spanning-tree vlan 'vlan-num' cost 'cost'`

    * `spanning-tree vlan 'vlan-num' port-priority 'port-priority'`


