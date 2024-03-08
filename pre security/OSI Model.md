
OSI (open system interconnection) is a model providing a framework dictating how devices in the network receive, send and interpret data.

**Application**
=
A layer where rules and protocols about how the user should interact with data sent or received is written.

**Presentation**
=
A layer where standards for applications/ software is written. This standard is crucial for interoperability between different systems and devices.
the layer acts as a translator, that translates data from and to application layer and the device.

Session
=
Concerns with the creation of a connection(session) with other devices.
Synchronization and chopping of a data into smaller chunks take place.

Transport
=
Come into play in the action of transmitting data across the network, so to say across the session created in the previous layer
- TCP
- UDP
are the two main protocols in action in this layer
Network
=
A layer where routing and re-assembly of data takes place.
Protocols at this layer are concerned with finding the optimal path for the [packet](Packet&Frame.md#Packer) transmission. 
- RIP
- OSPF are some to mention

Data Link
=
This layer concerns with linking(attaching) a physical address(MAC address - that's engraved on the NIC) to the packet received. Thereby creating 
[[Packet&Frame#^Frames]]



Changing/presenting to a format that is suitable for transmission is also another job on the table for this layer.

Physical
=
Information is after all physical, if not for these physical components we have no chance of enjoying the day under the bath of information. 
These network devices use electrical signals to transfer the 0s and 1s.









