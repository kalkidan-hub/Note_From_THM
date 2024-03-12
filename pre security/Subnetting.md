## Subnetting



*what is subnetting?*

A process of changing the larger one network into smaller, minute different and isolated network.

*how it's achieved?*

By splitting up the number of hosts that can fit within the network, which is represented by a subnet mask. 
IP address is used in three ways in subnetting...
- Network Address - the starting address of the sub-network
- Host Address - an IP address of the devices within the subnet
- Default Gateway - an IP address of the device that represents the subnet, that's capable to send the information to another network.

*why subnetting?*
- efficiency
- better control
- security

## The APR Protocol

Address resolution protocol - resolves(maps) an ip address for a MAC address

*how does it works?*

by constantly updating the ARP cache/table.
1. a packet to specific IP address reaches the gateway - where the ARP cache is usually maintained
2. the gateway device checks for the MAC address associated with that ip address
3. if the mac address is found, wella it sends it directly to that devices, but if not...
4. ARP request is sent to all devices within the network, which says "who has this ip address?", and the device with the specified ip address replies with his MAC address, saying "Oh! it's mine, and remember that very fact with this MAC address."
5. the router updates its ARP cache accordingly.

## DHCP(Dynamic Host Configuration Protocol)

- Here are the series of actions(protocol) that enable a device to connect to a network(in the light of dhcp) - note that a device to be connected to a given network it has to have a network address which belongs to that network.
1. A device sends out a request ==DHCP Discovery== to see if there's any DHCP server. - this is a packet with the destination address of  broadcast address ``` 255.255.255.255``` 
2. The DHCP server sends replies back with the ip addresses to use. ==DHCP Offer==
3. The device sends the ==DHCP Request== confirming the server it wants the offered ip address
4. The DHCP server sends the acknowledgement reply ==DHCP ACK== marking the completion,

