# CCNA Part 31

## IPv6 Part 1

### Agenda:

* Why IPv6?

* Basics of IPv6

* Configuring IPv6 addresses

#### What about IPv5?

* Internet stream protocol was developed in the late 1970s, but never actually intaduced for public use.

* It was never called 'IPv5', but it used the value of 5 in the version field of the IP header.

* So when the successor to IPv4 was being developed it was named IPv6.

#### Why IPv6?

* There aren't enough IPv4 address available.

* VLSM, private IPv4 addresses, and NAT have been used to conserve the use of IPv4 address space, but are short term solutions.

* The longterm solution to not run out of addresses is to switch to IPv6.

* IPv4 address assignment are controlled by IANA

* IANA Distrabutes IPv4 address space to various RIRs(Regional Internet Registers), which then assign them to companies that need them.

#### IPv6

* 128 bits.

* 32 Hex chars

* IPv6 always uses `/` to show networks

* Shoertening IPv6 addresses:

    * Leading 0s can be removed

    * Cinsecutive quartets of all 0s can be replaced by double colon `::`

    * this can oly be done once in the address space.

    * EX.

        * 2000:AB78:0020:01BF:ED89:0000:0000:0001 = 2000:AB78:20:1BF:ED89::1

        * FE80:0000:0000:0000:0002:0000:0000:FBE8 = FE80::2:0:0:FBE8

        * AE89:2100:01AC:00F0:0000:0000:0000:020F = AE89:2100:1AC:F0::20F
    
* Expaning shortened IPv6 Address:

    * Put leading 0s where needed

    * If a double colon is used, replace it with all-0 quartets. 8 quartets are in IPv6

    * EX:

        * FE80::1010:2FC:0:9 = FE80:0000:0000:0000:1010:02FC:0000:0009

        * FF02::2 = FF02:0000:0000:0000:0000:0000:0000:0002

        * ::1 = 0000:0000:0000:0000:0000:0000:0000:0001 

* Finding the IPv6 prefix

    * Typically, and enterprise requesting IPv6 addresses from their ISP will recieve a /48 block.

    * Typically, IPv6 subnets use a /64 prefix length.

    * That means an enterprise has 16 bits to use to make subnets.

    * The remaining 64 bits can be used for hosts.

#### Configuring IPv6 Addresses

* `ipv6 unicast-routing` - Allows router to perform IPv6 routing.

* `int INTERFACE`

* `ipv6 address IPv6 ADDRESS/PREFIX`

* `no shotdown`

* each interface will have 2 IPv6 address when config IPv6 a link-local addresses will be set