#CCNA Part 13

## Subnetting Part 1

### Agenda:

* CIDR (Classes Inter-Domain Routing)

* The process of subnetting

---

* IANA = The Internet Assigned Numbers Authority assignes IPv4 addresses/networks to companies based on their size.
    
    * For example, a very large company might recive a class A or class B network, while a small company might recieve a class C network.

* This system has led to many wasted IP addresses.

* Point to point netwroks are networks that connect two routers.

* Address waste usually occurs when the host number is less than 255.

* Subnetting makes it possible to keep address space wate to a minimum.

### CIDR(Class Inter-Domain Routing):

* With CIDR, the requirments of Class A = /8, Class B = /16, Class C = /24 were removed.

* This allowed networks to be split into smaller networks, allowing greater efficency.

* These smaller networks are called 'subnetworks' or 'subnets'.

#### EX.

* Calculate usable address number for each network.

1) /25 = 126

2) /26 = 62

3) /27 = 30

4) /28 = 14

5) /29 = 6

6) /30 = 2

7) /31 = 0 (for point to point links this subnet mask can be used.)

8) /32 = 0 (this would be a local address for a router.)

--- 

* The notation above is called CIDR Notation.




