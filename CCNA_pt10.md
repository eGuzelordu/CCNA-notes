# CCNA Part 10

## The IPv4 Header

### IPv4 Header:

* Min length 20 bytes.

* Max length 60 bytes.

#### Version Field:

* 4 bits

* Identifies the version of IP used.

    * IPv4 = 4 (0100)

    * IPv6 = 6 (0110)

#### Internet Header Length(IHL):

* 4 bits

* The final field of the IPv4 header(Options) is variable in length, so this field is necessary to indicate the total length of the header.

* Identifies the length of the header in 4-byte increments.

* Min value is 5(20 bytes) and the Max value is 15(60 bytes).

#### Diffrectiated Services Code point (DSCP):

* 6 bits

* Used for QoS(Quality of Service).

* Used to prioritize delay-sensitive data(streaming voice, vid, etc.)

#### Explicit Congestion Notification (ECN)

* 2 bits

* Provides end-to-end notification of network congestion without dropping packets.

* Optional feature that requires both endpoints, as well as the underlying network infrastructure, to support it.

#### Total Length:

* 16 bits

* Indicates the total length of the packet(L3 Header + L4 segment).

* Measured in bytes (not in 4-byte increments like IHL).

* Min Val is 20(bytes) max val is 65535(bytes).

#### Identification:

* 16 bits

* If a packet is fragmented due to being too large, this field is used to identify which packet the fragment belongs to.

* All fregments of the same packet will have their own IPv4 header with the same value in this field.

* Packets are fragmented if larger than the MTU(Max Transition Unit)

* The MTU is usually 1500 bytes.

* Fragments are reassembled by the receiving host.

#### Flags:

* 3 bits 

* Used to Control/identify fragments.

* Bit 0: Reserved, always set to 0.

* Bit 1: Dont Fragment(DF bit), used to indicate a packet that should not be fragmented.

* Bit 2: More Fregments (MF bit), set to 1 if there are more fragments in the packet, set to 0 for the last fragment.

* Unfragmented packets will have both Bit 1 and 2 as 0

#### Fragment Offset:

* 13 bits

* Used to indicate the position of the fragment within the original unfragmented IP packet.

* Allows Fragmented packets to be reassembled even if the fragments arrive out of order.

#### Time to Live:

* 8 bits

* A router will drop a packet with a TTL of 0.

* Used to prevent infinite loops when TTL reaches 0.

* Originally designed to indicate the packet's max lifetime in seconds.

* In practice, indicates a 'hop count': each time the packet arrives at a router, the router decreases the TTL by 1.

* Reccomended TTL is 64.

#### Protocol:

* 8 bits

* Indicates protocol of the encapsulated L4PDU.

* Value of 6: TCP.

* Value of 17: UDP. 

* Value of 1: ICMP.

* Value of 89: OSPF(dynamic routing protocol).

#### Header Checksum:

* 16 bits

* A calculated checksum used to check for errors in the IPv4 header.

* When a router recives a packet it calculates the checksum of the header and compares it to the one in this field of the header.

* If the checkdums dont match the router drops the packet.

* This is only used for the IPv4 header errors only.

* IP relies on the encapsulated protocol to detect errors in the encapsulated data.

* Both TCP and UDP have their own checksum fields to detect errors in the encapsulated data.

#### Source and Destination IP address:

* Both are 32 bits.

* Source is the IP address of the host that sent the packet.

* Destination is the IP address of the reciever of the packet 

#### Options Field.

* 0 - 320 bits

* Rearly used

* If IHL field is greater than 5 it means that Options are present.

