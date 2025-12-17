1. Host creates packet to send
2. Host checks if destination is in the LAN
	Does this by checking the IP address/mask to determine the rang of addresses
	in the local subnet, compares that range to the destination IP then chooses.
3. If the destination is outside the local subnet it sends it to the default gateway
	1. Find the default gateways MAC address using ARP table entry
	2. Or use APR messages to learning information
4. Else sends it to the destination
	1. To send locally find the destination hosts MAC address using ARP table entry
	2. Or use ARP messages to learn the information
5. Encapsulate the IP packet in a data link frame with the destination data link address
6. When the router receives the frame is decides whether to process it or not
	1. If it has no errors and is for the router it will process it
7. The router then gets the destination IP and compares it to the routing table
8. It then finds a route that matches the destination address
9. The router then encapsulates the packet and sends it
	1. If the next devices MAC address is not in the ARP cache of the router
	2. An ARP request will be used

SIMPLIFIED:
The router receives the frame, removes the packet from inside the frame, decides
which interface to forward the packet out of, puts the packet into another frame,
and sends the frame (with the packet inside it) out the correct router interface.