# CCNA part 8

## IPv4 Addressing Part 2

* The number of usable addresses are the number of addresses - 2 first address is the netwrok address and the last address is the broadcast address.

#### Configure a Cisco Router:

* `show ip interface brief` = this command gives Interfaces, the IP-Address, OK?(a legacy fauture), Method(what method was used to assign IP), Status(Layer 1 status of interface), Protocol(layer 2 status).

* `interface interface-name` = gets you in interface config mode reperesented by `Router(config-if)#`.

* 

## Step by step how to set up a router on Cisco ISO CLI

1) `enable` - get into privaliged EXEC Mode.

2) `interface interface-name` - gets into config interface mode on the given interface.

3) `ip address ip-address subnet-mask` - assigns switch to router.

4) `no shutdown` - changes the setting to boot up the routers.