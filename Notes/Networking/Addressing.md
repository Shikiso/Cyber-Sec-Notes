**Default gateway** -> Usually the routers IP address, but any host that allows traffic to escape the network is a gateway.

**IPv4**
- 32bit addresses
- Uses binary to create addresses
- Each octet can range from 0-255

**IPv6**
- can have more than one on an interface 
- 0-9 A-F
- separate by : 
- 128 bits in length

**Network Classes**
A /8	<- 255.0.0.0			<- Host
B /16	<- 255.255.0.0			<- Host
C /24	<- 255.255.255.0		<- Host
D /20	<- 224.0.0.0 - 239.0.0.0.0	<- Multicast
E /24	<- 240.0.0.0 - 255.0.0.0	<- Testing

A subnet mask is used to determine the host and network portion of a address.
255.255.255   .0
  ^ Network  ^ Host
192.168.1       .1
^ Network   ^ Host
Each digit before . is an octect (8 bit positions)

IPv4 networks can not use the first and last address because:
- Network address is the first address in a network: 192.168.10.0
- Last Network address is a broadcast address

## Subnet Maks
Subnet Mask		32-bit Address			Prefix Length
255.0.0.0       11111111.00000000.00000000.00000000		/8
255.255.255.192 11111111.111111111.11111111.11000000		/26
		    ^8     ^8        ^8      ^2

Within each network there are 3 types of IP address
	- Subnet mask		255.255.255.0
	- Network address	192.168.10.0
	- Host addresses	192.168.10.1-254
	- Broadcast address	192.168.10.255

## Different Addresses
Private IP addresses are assigned to devices inside a LAN
/8 /12 /16 are private addressing prefixes
Outside networks can see private IP address pools

Private addresses:
10.0.0/8	10.0.0.0 - 10.255.255.255
172.16/12	172.16.0.0 - 176.31.255.255
192.168/16	192.168.0.0 - 192.168.255.255

Layer 3 addressing does not change unless NAT occurs
Network Address Translation (NAT) - Converts private IP to public IP

Loopback address: 127.0.0.1 used to test if TCP/IP is operations (checks if OSI operation is working)

Link-Local address:
	- 169.254.0.0/16 (169.254.0.1 - 169.254.255.254)
	- used by clients to self configure when no DHCP servers are available
	- Can communicate locally but not outside the network

If to many broadcast requests are made it will affect the negatively.
To reduce the amount of broadcasts you can split the network using a router

CIDR or Classless Inter-Domain Routing is a method of allocating IP addresses and routing Internet Protocol Packets in a more flexible and efficient way. CIDR achieves its goals by replacing the traditional class addressing schemes with a system that allows for variable length subnet masking (VLSM).

A CIDR notation looks like this: `192.168.1.0/24`. Here, `192.168.1.0` is the IP address, and `/24` represents the subnet mask.

