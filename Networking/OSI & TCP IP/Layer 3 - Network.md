Network layer 3 multiple such as protocols IPv4, IPv6, Open Shortest Path First (OSPF),
Internet Control Message Protocol (ICMP).

Network layer performs 3 operation to accomplish end-to-end communication:
	Addressing end devices - end devices must have unique IP for identification
	Encapsulation - encapsulates the protocol data unit (PDU) from the transport layer into a packet
			Adds IP header info (source, destination)
	Routing - Directs packets to destination host on another network. To travel to other network packet
			must be processes by a router. Router is to select best path and send packets
	De-encapsulation - When the packet arrives at the network layer, the host checks the IP header of 
				the packet. If the destination IP matches its own IP, the IP header is removed.

IP packet will be examined by all layer 3 devices

IP was not designed to track and manage flow of packets. (Layer 4 does this)
Basic characteristics of IP:
	- Connectionless: There is no connection destination established before sending data packets
	- Best Effort: IP is inherently unreliable because packet delivery is not guaranteed.
	- Media Independent: Operation is independent of the medium carrying the data.

Fragmentation - Splitting up an IP packet when forwarding it from one medium to another medium.

Subnet mask defines where the network boundary is

Network		Host
192.168.1	.1
255.255.255	.0

192.168		.20.1
255.255		.0.0

IPv4 Problems:
	- Address depletion
	- Lack of end-to-end connectivity
	- Increased network complexity

IPv4 Packet
Version - Identifies this as IPv4 packet
Differentiated Services or DiffServ (DS) - Determines priority of each packet.
Time to Live (TTL) - Limit lifetime of a packet.
Protocol - Identify next protocol
Internet Header Length (IHL) and Header Checksum used to identify and validate the packet.
Source - Where the packet came from
Destination - Where the packet is being sent to

IPv6 pros:
	- Increased address space
	- Improves packet handling
	- Eliminates the need for NAT

IPv6 Packet
Version - Identifies this as IPv6 Packet
Traffic Class - DS
Flow Label - Suggests all packets with same flow label receive same type of handling
Payload Length - Length of data
Next Header - Indicates data payload type
Hop Limit - TTL
Source
Destination

Packet created at source
Communicate established at host
each host device creates its own routing table
layer 2 for own network
has to go through router for separate network
router redirect traffic
if host doesn't know where to send data it sends it to default gateway
default gateway sends data out the network

octect - Number/Hex in IP address
192.168.1.1
^    ^  ^ ^	
octect

Host can direct packets to:
	- Itself (Loop Back): A host can ping itself by sending a packet to a special IPv4 127.0.0.1 or IPv6 ::1
	- Local Host: destination host that is on the same local network
	- Remote Host: Destination host on a remote network

On Windows can view the Host routing table with "netstat -r" or "route print"
Interface List - MAC address and assigned interface number of every network-capable interface on host
IPv4 Route Table - Lists all know IPv4 routes
IPv6 Route Table - ^ IPv6 routes

Host will know the default gateway either statically or though DHCP in ip

IP Router Routing Table
	- Directly-connected networks: active router interfaces that are added automatically
	- Remote networks: Routes the routers doesn't have a direct connection, can be learned
		- Manually: static route
		- Dynamically: using routing protocol to have the routers share their info
	- Default route: last resort, sends all traffic to a specific direction when no match in routing table
	- Loop back address

Router can learn about remote networks in two ways:
	Manually: Manually entered into the route table using static routes
	Dynamically: Automatically learned using a dynamic router protocol

Static routes: IMPORTANT
	- Must be configured manually
	- Admin needs to reconfigure if there is a change in the topology and the route is no longer viable
	- Appropriate for a small network, when few or no redundant links

Dynamic routing protocol:
	- Includes OSPF and Enhanced Interior Gateway Routing Protocol (EIGRP)
	- Discover remote networks
	- Maintain up-to-date routing information
	- Choose best path to destination networks
	- Attempt to find a new best path if the current path is no longer available

show ip route - show routing table on cisco IOS router
L - Directly connected local interface IP address
C - Directly connected network
S - Static route was manually configured by an administrator
S* - Default Route
O - OSPF
D - EIGRP
