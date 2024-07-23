# CCNA part 9

## Switch Interfaces:

* switch interfaces do not have the `shutdown` as default so if they are not connected it will show `down/down`

|Port|Name|Status|Vlan|Duplex|Speed|Type|
|---|---|---|---|---|---|---|
|Lists each interface|Description of the interface|Shows if connected or not|Later Topic|Indicates if the device is capable of sending and reciving|Speed of the device|type of ethernet used|

#### Half Duplex:

* the device cant send and recieve data at the same time, it must wait before sending a frame.

* Devices attached to a hub nust oparate in half duplex.

#### Full Duplex:

* The device can send and receive data at the same time. it does not have to wait.

* Devices attached to a switch can operate in full duplex.

### Hub:

* A LAN Hub is basic repeaters that dont use MAC addresses.

* are seceptable to collision.

* in order to deal with these collison a protocol named CSMA/CD is used.

#### CSMA/CD

* Carrier Sense Multiple Access with collision Detection.

* Before sending domains, devices 'listen' to the collision domain until they detect that the other devices are not sending.

* If a collision does occur, the device send a jamming signal to infrom the other devices that a collision happend.

* each device will wait a random amount of time before sending frames again.

* the process repeats.

* used in half-duplex.

#### Speed/Duplex Autonegetiation

* Interfaces that can run at diffrent speeds(10/100 or 10/100/1000) have default setting of `speed auto` and `duplex auto`

* Interfaces 'advertise' their capabilities to the neighboring device, and they negotiate the best `speed` and `duplex` settings they are both capable of.

* what is autonegotiation is disabled on the device connected to the switc>

    * The switch will try to sense the speed that the other device is operating at. If it fails to sense the speed it will use the slowest supported speed 

    * Duplex: if the speed is 10 or 100 Mbps, the switch will use half duplex. If the speed is 1000 Mbps or greater, use full duplex.


---

* Runts: Frames that are smaller than the min frame size(64 bytes).

* Giants: Frames that are larger than the max frame size(1518 bytes).

* CRC: Frames that Failed the CRC check (in the Ethernet FCS trailer).

* Frame: Frames that hace an incorrect format (due to an error).

* Input errors: Total of various counters, such as the above four.

* Output errors: Frames the switch tried to send, but failed due to an error.

