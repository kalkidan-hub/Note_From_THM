

Methods and technologies to extend out the local network and services onto the internet.

Port Forwarding
=
Is an application of ==NAT== that redirect a communication request from one ip address and port combination to another while packets are traversing through network gateway, such as router and firewall. 

Firewalls
=
A device within a network that determines which packet pass though and which don't based on the the setting granted to them.
We have two categories of them, 
- stateful - where decision is made based on the entire connection's status
- stateless - where individual packets are examined to pass the decision, and the decision doesn't depend on the state the packet is in.


VPN (Virtual Private Network)
=
A technology that enable devices from different networks communicate securely by creating a dedicated path, known as tunnel - and thereby they create their own private network.
Benefits harnessed from VPN
- privacy
- anonymity
- networks from different geographical location can come together as if they are at the same local network - this has significance in business operation. 

We have some VPN technologies out there
- PPP - point to point
- PPTP - point to point tunnel protocol 
- IPSec

LAN networking devices
=
### Router
Routers are devices that connect ==networks==, not hosts but networks.
Their main function is to route a packet across the network, this involves choosing the best route, abiding to the configuration rules and so on.

>[!Tip]
>NAT traslation table and port forwarding methods are used together to map the private ip address with the packet that reaches at the gateway.



### Switch

Networking devices that provide a means to connect multiple devices. 
They operate both on layer 2 and layer 3. When they are at layer 3 they are primarily used to create VLAN(Virtual LAN) - splitting up devices in the LAN network as if they are in different network, in which case the switch acts as a router. 
