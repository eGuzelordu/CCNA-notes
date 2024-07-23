# CCNA Part 7

## IPv4 Adressing Part 1

### Layer 3 Review:

* Provides connectivity between end hosts on diffrent networks.

* Provides logical addressing(IP addresses).

* Provides path selection between source and destination.

* Routers oparate at Layer 3.

### Routing:

* Routers need an IP adress for each network its connected to.

### IPv4:

* IP addresses are 4 bytes

* The traditional way to display this is write 4 decimal number that each equal to their byte.

* the `*.*.*/*` the part after the `/` is used to specify how many bits are used for networks and the rest is used for hosts.

    * EX. `192.168.1.254/24` 
        * binary for it is `1100 0000 1010 0010 0000 0001 1111 1110`
        * the first 24 bits represent the network adress `1100 0000 1010 0010 0000 0001`
        * and the last 8 bits represent the host address `1111 1110`
        * in this network there are 2^24 - 2 network addresses and 2^8 - 2 hosts addresses.

    * EX `154.78.111.32/16` 
        * binary for it is `1001 1010 0100 1110 0110 1111 0010 0000`
        * the frist 16 bits are `1001 1010 0100 1110` this is the network address which is `154.78.0.0`
        * the last 16 bytes are `0110 1111 0010 0000` this is the host address which is `154.78.111.32` 

* The smaller the prefix is the more hosts the network can fir in it

* The larger the prefix is the more networks we can store.

* the first address in each network is the Network address and the last adress in the network is the broadcast address there for there are 2^(32-prefix#) - 2 addresses available per network.

#### IPv4 Address Classes

|Class|First Octet|First Numeric Range|Prefix Length|
|---|---|---|---|
|A|0XXX XXXX|0-127|/8|
|B|10XX XXXX|128-191|/16|
|C|110X XXXX|192-223|/24|
|D|1110 XXXX|224-236||
|E|1111 XXXX|240-255||

* Addresses on Class D will be reserved for Multicast addresses.

* Addresses on Class E will be reserved for experimental usage.

* cisco uses a diffrent way to write the prefix
    * on a 32 bit grid if the prefix is X then the first X bits will be a 1 and it is written like an ip address
        * EX. /8 `1111 1111 0000 0000 0000 0000 0000 0000` in Cisco devices would be written as `255.0.0.0`
        * Ex. /16 `1111 1111 1111 1111 0000 0000 0000 0000` in Cisco Device would be written as `255.255.0.0`

#### LoopBack Addresses:

* Address range 127.0.0.0 - 127.255.255.255

* Used to test the `Network Stack` (think OSI, TCP/IP model) on the local device.



#### Network Address:

* Host portion of the address is all 0's

* The network address can not be assigned to a host.

#### broadcast Address:

* Host portion of the address is all 1's

* The network address can not be assigned to a host.
