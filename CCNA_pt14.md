# CCNA Part 13

## Subnetting Part 2

* when choosing to make subnets for X amount of networks then we find the least amount of bits that will allow that many networks.

* Example in a Class C netwrok that needs 5 subnets what would be the subnet mask?

    * it would be /27 due to we need 3 bits to have 5 subnets configured.

    * The subnets would be as followed if the class C network address is 192.168.255.0/24

        1) Subnet 1: 192.168.255.0/27 - 192.168.255.31/27

        2) Subnet 2: 192.168.255.32/27 - 192.168.255.63/27

        3) Subnet 3: 192.168.255.64/27 - 192.168.255.95/27

        4) Subnet 4: 192.168.255.96/27 - 192.168.255.127/27

        5) Subnet 5: 192.168.255.128/27 - 192.168.255.159/27

* What Subnet does Host 192.168.5.57/27 belong to?

    57 = 0011 1001

    Subnet 27 occupies 3 bits in the last octet therefore the subnet ID would be:

    `192.168.5.32`

* What Subnet does Host 192.168.29.219/29 belong to?

    219 = 1101 1011

    Subnet 29 occupies 5 bits in the last octet therefore the subnet ID would be:

    `192.168.5.216/29`

---

### Class B Subnetting.

* It works exactly the same as the class C but the starting netMask is /16 instead of /24

* Example create 80 Subnets for this company in this class B network.

    172.16.0.0/16

    we will need 7 bit bc 2^6 < 80 < 2^7

    so the subnet mask would be /23 or 255.255.254.0


* Example create 500 Subnets for this company in this class B network.

    172.22.0.0/16

    we will need 9 bits bc 2^8 < 500 < 2^9

    so the subnet mask would be /25 or 255.255.255.128


* Example create 500 Subnets for this company in this class B network.

    172.28.0.0/16

    we will need 9 bits bc 2^7 < 250 < 2^8

    so the subnet mask would be /24 or 255.255.255.0

* What Subnet does Host 172.25.217.192/21 belong to?

    217.192 = 1101 1001 1100 0000

    Subnet 21 occupies 6 bits in the second last octet therefore the subnet ID would be:

    `192.168.216.0/21`


#### QUIZ Answers:

1) /23 255.255.254.0

2) 172.21.96.0

3) 192.168.91.127/26

4) 172.16.64.0 - 172.16.127.255

5) 2^6 = 64
