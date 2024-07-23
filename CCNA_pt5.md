# CCNA part 5

## Ethernet LAN Switching Part 1

* Ethernet includes layer 1 and layer 2.

* LAN = network contained in a reletivey small area.

### Ethernet header and the trailer:

#### Header:

* 5 fields in the header.

* Preamble

    * Length 7 bytes (56 bit)
    * Alternating 1's and 0's
    * Each byte in it looks like `10101010`
    * Allows devices to synchronize their reciver clocks.

* SFD Start Frame Delimiter

    * Length is 1 byte (8 bits).
    * The byte looks like `10101011`.
    * This marks the end of the preamble, and the beggining of the rest of the frame.
    
* Destination & Source

    * destination and source are both 6 bytes(48 bits)
    * Indicate the devices sending and receiving the frame.
    * consist of the Destination and source `MAC addess`.
    * MAC = Media Access Control
    * the MAC adress is 6 bytes (48 bits) long and is the adress of the physical device.

* Type or Length

    * 2 bytes (16 bits)
    * It can indicate the type or length of the packet. 
    * If the value of the field is 1500 or less it indicates the length of the encapsulation(in bytes).
    * If the value of the field is 1536 or greater it indicates the type of the encapuslation packet, and the length is determined via other methods.


#### Trailer

* Only has one field.

* FCS Frame Check Sequance

    * 4 bytes in length (32 bits)
    * Detects corrupted data by running a `CRC` algo over recived data.
    * CRC = Cyclic Redundency Check.

#### MAC Adress

* 6-byte physical address assigned to the device when its made.

* A.K.A. Burned-In Address

* Is globally Unique.

* The first 3 bytes are the OUI(Organizationally Unique Identifier), whihc is assigned to the company making the device.

* the last 3 Bytes are unique to the device itself

* written as 12 Hex chars

* Dynamically learned mac address: when the switch will learn the address on its own. This is done by looking at the source and destination on the header on the frame.

* Every switch has a MAC Address Table to keep tabs on the devices.

* If the mac adress is not on the MAC Address Table then the switch flood to all routes that are unkown.


#### Side Notes:

* Unitcast Frame: a frame destined for a single target.

* Unknown Unicast Frame: It floods the network to hit the destination

* Known Unicast Frame: Since the destination is already on the MAC Address Table it send the packet only to the destination host. It forwards it.

* On cisco switches Dynamic MAC addresses are removed from the MAC address table after 5 minutes of inactivity.



## QUIZ QUESTIONS:

1) Which Field of an Ehternet frame provides receiver clock synchronization?

(a) Preamble

(b) SFD

(c) Type

(d) FCS

2) How long is the physical address of a network device?

(a) 32 bytes

(b) 32 bits

(c) 48 bytes

(d) 48 bits

3) What is the OUI of this MAC adress? E8BA.7011.2874

(a) E8BA

(b) E8BA.70

(c) 7011

(d) E8BA.7011

4) Which fireld of an Ethernet frame does a switch use to populate its MAC address table?

(a) Preamble

(b) Length

(c) Source MAC address

(d) Destination MAC address

5) What kinf of a frame does a switch floog out of all interfaces expect the one it was recived on?

(a) Unknown Unicast

(b) Known unicast

(c) Allcast