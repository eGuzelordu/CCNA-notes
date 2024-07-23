# CCNA Part 3 

## OSI MODEL & TCP/IP SUITE

### Networking Model:

* Networking models categorize and provide a structure for networking protocols and standards.


### OSI Model:

* A conceptual model that categorizes and standardizes the diffrent functions in a network.

* it was created by ISO.

* divided into 7 layers.

|Layer|Purose|
|---|---|
|7. Application| - Layer thats closest to the end use</p>- Interacts withe the software applications, for example the we browser </p>- HTTP and HTTPS are Layer 7 protocols.</p>- Identifying communication partners, and Synchronizing communication are functions of layer 7|
|6. Presentation| - Data in the application layer is in application format</p>- It needs to be 'translated' to a diffrent format to be sent ober the network. </p>- The presentation layer's job is to translate between application and network formats. for example encryption data as it is send, and dycryption data as it is received.</p>- Also translates between diffrent Application-Layer formats.|
|5. Session|- Controls dialofues(sessions) between communication hosts.</p>- Establishes; manages and terminates connection and the remote application.|
|4. Transport|- Segments and reassembles data communications between end host</p>- Breaks large pieces of data into smaller segments which can be more easily sent over the network and are less likely to cause transmission problems if errors occur</p>- Provide host-to-host communication.</p>- Data + the L4 header is a called a segement(if data being sent too big it will segment into diffrent pieces and the L4 header will be added to each data block).|
|3. Network|- Provides connectivity between end hosts on different networks(outside of LAN)<\p>- Provides logical addressing(IP addresses).</p>- Provides path selection between source and destination</p>- Routers oparate at L3</p>- When a L3 header is added to a segment it is called a packet|
|2. Data Link|- Provides node-to-node connectivity and data transfer</p>- Defines how data is formatted for transmission over a hysical medium</p> Detects and corrects Physical Layer errors.</p>- Uses Layer 2 addressing, searate from layer 3 addressing.</p>- Switches oparate at L2.</p>- When a L2 Header and a trailer are added to a packet it becomes a frame|
|1.Physical|- Defines physical characteristics of the meduim to transfer data between devices</p>- For example voltage levels, max transmission distance, physocal connectors, cable specification, etc.</p>- Digital bits are converted into electrical or radio signals.|



* Data, Segments, Packets, and Frames are all Protocol Data Units(PDUs).

* Layer 1 PDU is a bit.

### TCP/IP Suite:

* Conceptual model and set of communications protocals used in the internet and other networks.

* Known as the TCP/IP because those are two of the foundational protocols in the suite.

* Developed by the US Department of Defense thorugh DERPA(Defence Advanced Research Projects Agency).

* Similar to the OSI Model but with fewer layers.

* This model is actually used in networks.

|Layers|Purpose|
|---|---|
|4. Application|Combines Application, Presentation, and Session Layer form the OSI|
|3. Transport|Same as the OSI|
|2. Internet|Same as the Network layer from the OSI|
|1. Link|Combines Data Link and Physical Layer from the OSI|

#### Side notes:

* protocols are a set of rules defining how network devices and software shuold work.

* uptil this point everything weve learned is in layer 1 (pysical layer).

* network enginners dont really work with the top 3 layers it is mostly done by software engineers.

* Adjecent-Layer interation: interection between diffrent levels of the OSI model

* Same-Layer interection: interection between same layer on diffrent hosts.

* application layer provides process-to-process communication.

* the transport layer provides host-to-host communications.

#### Directory:

* OSI = Open System Interconnection

* ISO = International Organization for Standardization

* Adjacent-layer interection = interection between the diffrent layers of the OSI model.
