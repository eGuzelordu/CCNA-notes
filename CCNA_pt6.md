# CCNA part 6

## Ethernet LAN Switching Part 2

* The Preamble + SFD is usally not considered part of the ehternet header.

* The ethernet header consists of these three fields:

    * Destination

    * Source

    * Type

* the size of the Ethernet header + trailer is 18 bytes (6+6+2+4)

* the minimum size of a ethernet frame is 64 bytes. this doesn't include Preamble and the SFD.

* the minimum payload (packet) size is 46 bytes.

* if the payload(packet) size is less than 46 bytes padding bytes are added

* padding bytes are all 0's

### ARP (Address Resolution Protocol)

* Is used to discover the layer 2 MAC address of a known Layer 3 IP address

* Consists of two messages:

    * ARP request:

        * Sent as Broadcast(sent to all hosts on the network)

    * ARP reply:
        * Sent as a Unicast (only to one host, the host that sent request).

### Ping

* a network utility that is used to test reachability.

* Measures round-trip time

* Uses two messages:

    * ICMP Echo Request 
        * The pc will not broadcast this request it has to already know the MAC of the host in order to perform a ping.

    * ICMP Echo Reply

* Command to use ping: `ping (ip-address)`

* By default Cisco IOS send s 5 100-byte Echos.

* `.` is Failed ping `!` is successful ping.

* `show arp`: show arp log 

* `show mac address-table` shows MAC address table.

#### MAC Address Table:

* VLAN

    * Virtual Local Area Network.

* MAC address

    * Shows the MAC adresses that the device remembers.

* Type

    * Shows how the MAC address was aquired(Dynamic, static etc.).

* Ports

    * What port to forward for sending frame.

* `clear mac address-table dynamic` = gets rid of dynamic addresses.

    * if added an ip adress at the end of it it will get rid of only that 

    * the same thing can be done with ip adresses that come from the same port.
 
#### Side Notes:

The broadcast address used for dest MAC is : `FFFF.FFFF.FFFF`