# CCNA Part 23

## Ether Channel

### Agenda

* What is EtherChannel? What problem does it solve?

* Configuring Layer2/layer3 EtherChannels

#### EtherChannel

* If you connect two switches together with multiple links all except one will be disabled by spanning tree.

* Represented by a circle drawn around the links between connections

* When an ether channel is activated STP will treat this group as a single interface.

* Traffic using the EhterChannel will will be load balanced amog the physical interfaces in the group. An algorithm is used to determine which traffic will use which physical interface.

* Some other names for an EtherChannel are:

    * Port Channel

    * LAG(Link Aggregation Group)

* EhterChannel Load-Balancing

    * EtherChannel load balances based on 'flows'.

    * A flow is a communication between two nodes in the network.

    * Frames in the same flow will be forwarded using the same physical interface.

    * If frames in the same flow were forwarded using diffrent physical interfaces, some frames may arrive at the destination out of order, which can cause problems.

    * You can change the inputs used in the interface selection calculation.

    * Inputs can be used:

        * Source MAC

        * Destination MAC

        * Source and destination MAC

        * Source IP

        * Destination IP

        * Source and destination IP

* Configuring EtherChannel Load-Balance

    * `show etherchannel load-balance` to show the Load-Balancing configuration.

    * `port-channel load-balance 'method'` to change the load balance config.

    * There are three methods of Etherchannell configuration on Cisco Switches:

        * PAgP(Port Aggregation Protocol)

            * Cisco Proprietary protocol.

            * Synamically negotiatis the creation/maintenance of the EtherChannel.(Like DTP does for trunks).

        * LACP(Link Aggregation Control Protocol)

            * Industry standart protocol(IEEE 802.ad)

            * Dynamically negotiaties the creation/matinence of the EhterChannel.(Like DTP does with trunks).

        * Static EtherChannel

            * A protocol isn't used to determine if an EtherChannel should be formed.

            * Interfaces are statically configured to form an EtherChannel.

    * Up to 8 interfaces can be formed into a single EhterChannel(LACP allows upto 16 but only 8 will be active, the other 8 will be in standby mode, waiting for an active interface to fail).

    * Inorder to configure:

        * `interface range interfaces`

        * `channel-group 'number' mode ?` the `?` can be the following:

            * active: actively try to establish a EtherChannel(LACP)

            * auto: doesnt actively try to establish a EtherChannel(PAgP)

            * desirable: actively try to establish a EtherChannel(PAgP) 

            * on: Enable Etherchannel only(Only works with On mode is not compatible with auto or desirable).

            * passive: doesnt actively try to establish a EtherChannel(LACP)

        * `channel-protocol 'protocol'` has two options:

            * LACP

            * pagp
        
        * `interface port-channel num`

        * `switchport mode trunk`

        * `do show interfaces trunk`

    * Member interfaces must have matching configs.

        * Same duplex

        * Same speed.

        * Same switchport Mode(Access/trunk)

        * Same allowed VLANs/Native VLAN(for trunk interfaces)

    * If and interface's configurations do not match the others, it will be excluded from the EtherChannel.

    * `show etherchannel summary` or `show etherchannel port-channel`- best ways to see config

    * Configure Layer 3 EhterChannel:

        * `no switchport`

        * `channel-group num mode 'mode'`

        * `int po'num'`

        * configure IP address as usual
