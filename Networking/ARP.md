ARP is local and IPv4

If a network uses IPv4 communications protocol, the Address Resolution Protocol (ARP) is used
to map IPv4 addresses to MAC address

Every IP device on ethernet network has unique MAC.

When device sends layer 2 frame it contains:
	- Destination MAC address
	- Source MAC address

To send a packet to another host on the same (IPv4) network a host must know
the IPv4 address and MAC address of the destination.

A device uses ARP to determine the destination MAC address when it knows it IPv4 address
ARP provides 2 functions:
	- Resolving IPv4 address to MAC address
	- Maintaining a table of IPv4 to MAC address mappings

When a packet is sent to layer 2 to be encapsulated into an Ethernet frame, the device refers to the ARP table/cache to find the MAC address that is mapped to the IPv4 address.

The sending device will search its ARP table for destination IPv4 address and a corresponding MAC address.
If the destination IPv4 address in on the same network as the source, the device will search the ARP table for the destination IPv4 address.

ARP table is wiped every 4 hours and can be wiped manually

If the device locates the IPv4 address, its corresponding MAC address is used as the destination MAC address in the frame. If there is no entry found, the device sends an ARP request.

An ARP request is sent when a device needs to determine the MAC address that is associated with an IPv4 address.
ARP messages are encapsulated directly within an Ethernet frame, there is no IPv4 header, the header info is:
	- Destination MAC
	- Source MAC
	- Type: 0x806

ARP requests are broadcasts meaning they are flooded out all ports by the switch, except the
receiving port. Every device must process the ARP request to see if the target address matches its own.

Only the device with the target IPv4 address associated will send a ARP reply.
ARP reply is encapsulated in an ethernet frame using the following header info:
	- Destination MAC address
	- Source MAC address
	- Type: 0x806

If destination IPv4 address not on same network the source device will send the frame to default gateway

Commands:
	SHOW ARP TABLE:
	CISCO router: show ip arp
	WINDOWS: arp -a

IPv6 uses Neighbor Discovery Messages
provides:
	- Neighbor Solicitation messages
	- Neighbor Advertisement messages
	- Router Solicitation messages
	- Router Advertisement messages
	- Redirect Message

Neighbor solicitation and advertisement messages are used for device-to-device messaging (similar to ARP)
