# CCNA Part 2

## Interface & Cables


### Ethernet

#### Offical Description:

* A collection of network protocols/standards.

---

#### Ehternet Standards:

* Defined in the IEEE 802.3 standarts in 1983

#### Ethernet standarts for Copper:

|   Speed   |   Common Name  | IEEE Standart |   Informal Name   | Max Length| Wires Used |
|---        |---             |---            |---                |---        |---|
| 10 Mbps   |   Ethernet     |   802.3i      |   10BASE-T        |   100 m   |2 pairs(4 wires)|
| 100 Mbps  | Fast Ethernet  |   802.3u      |   100BASE-T       |   100 m   |2 pairs(4 wires)|
| 1000 Mbps   |Gigabit Ethernet|   802.3ab     |   1000BASE-T      |   100 m   |4 pairs(8 wires)|
| 10000 Mbps   |10 Gig Ethernet |   802.3an     |   10GBASE-T       |   100 m   |8 pairs(8 wires)|

* BASE  = refers to baseband signaling.

* T = Twisted Pair cableing (max length is a 100m)

#### UTP Cables(10BASE-T, 100BASE-T):

|Device Type|Transmit(Tx) Pins|Receive(Rx) pins|
|---|---|---|
|Router|1 & 2| 3 & 6|
|Firewall|1 & 2| 3 & 6|
|PC|1 & 2| 3 & 6|
|Switch|3 & 6| 1 & 2|

* If the two devices being connected have the same Transmit and recive pins use a crossover cable or else use a straigt through cable.(older)

* Auto MDI-X makes it so that it will change the transmit and reciveing pins automatically so that no matter what the cable being used the tranmitting and the reciving will be fine.


#### UTP Cables(1000BASE-T, 10GBASE-T):

* each pair is bidirectional hance reciving and transmitting is made easier and is much faster


#### UTP Cables:

* UTP = Unshielded Twisted Pair

* Unshilded means it has no shield which means they are more suseptable to EMI

* Twisted pair protects against EMI



<hr style="border:1px solid gray">

### RJ-45 cords:

* it is used at the end of a copper ethernet cable

<hr style="border:1px solid gray">

### SFP Transceiver:

#### Fiber Optic Cables

* fiber optic cables are connected to it

* fiber optic cables use ligth over glass fibers

* Fiber optic only has to cables one to recive and one to transfer.

* fiber optic cable parts:
    1. the fiberglass core.
    2. cladding that reflects light.
    3. a protective buffer.
    4. outer jacket of the cable.


#### Multimode Fiber:

* Multimode core dieamiter is wider than sigle-mode fiber.

* Allows multiple angles(modes) of light waves to enter the fiberglass core.

* Allows longer cables than UTP, but shorter cables than single-mode fiber.

* Cheaper than single-mode fiber(due to cheaper LED-based SFP transmitters).

#### Single-mode Fiber:

* core diameter is narrower than multimode fiber.

* light enters at a single angle(mode) from a laser-based transmitter.

* allows longer cables than both UTp and multimode fiber.

* More expensive than multimode fiber (due to more expensive laser-based SFP transmitters)

#### Fiber-Optic Cable Standarts:

|Informal Name|IEEE Standard|Speed|Cable Type|Max Length|
|---|---|---|---|---|
|1000BASE-LX|802.3z|1 Gbps| Multi or Single-mode| 500 m(MM) / 5km (SM)|
|10GBASE-SR|802.3ae|10 Gbps|Multimode|400m|
|10GBASE-LR|802.3ae|10 Gbps|Single-mode|10 km|
|10GBASE-ER|802.3ae|10 Gbps|Single-mode|30 km|

#### UTP vs Fiber-Optic Cabling:

|UTP|Fiber-Optic|
|---|---|
|Lower cost|Higher Cost|
|Shorter Max distance|Longer Max length|
|Can be vulnerable to EMI|No vulneability to EMI|
|RJ45 ports used in UTP are cheaper than SFP ports|SFP ports are more expnsive|
|Emit(leak) faint signal outside of the cable which can be a security risk|Does not emit any signal outside of the cable|

#### Side Notes:

* network protocols and standarts are needed due to there having to be a world wide way for all hosts and servers to understand eachother. (this can be both physical and on a protocol level)

* a bit is a single binary digit such as a `0` or `1`

* a byte is 8 bits budled together representing a number between 255-0

* speed is mesured in bits per second

* kb = thousand bits / Mb = million bits / Gb = billion bits / Tb = trillion bits

* Stright through cables are cables that have RJ-45 heads where each pin is connected to the same pin number on the other side.

* Crossover cables are wired so that you can connect two of the same kind of ports to eachother and the pairings are as follows: 1<->3 / 2<->6 / 3<->1 / 6<->2 

<hr style="border:1px solid gray">

#### Directory:

IEEE: Institute of Electrical and Electronics Engineers

EMI: ElectroMagnetic Interference
