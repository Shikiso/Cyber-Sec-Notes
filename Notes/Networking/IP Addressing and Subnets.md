Default gateway: Allows your device access to other networks

IPv4: 192.168.1.20 | each number 0-255 | 8 bits in length
IPv6:
	- can have more than one on an interface 
	- 0-9 A-F
	- separate by : 
	- 128 bits in length
	- default gateway is the same as IPv4
-
CLASSES (Less network bits more host bits):
A /8	<- 255.0.0.0			<- Host
B /16	<- 255.255.0.0			<- Host
C /24	<- 255.255.255.0		<- Host
D /20	<- 224.0.0.0 - 239.0.0.0.0	<- Multicast
E /24	<- 240.0.0.0 - 255.0.0.0	<- Testing

subnet mask is used to determine the host and network portion
255.255.255 .0
  ^ Network  ^ Host
192.168.1   .1
^ Network   ^ Host
Each digit before . is an octect (8 bit positions)

IPv4 to Binary
192	  168	  10	   10
11000000 10100000 00001010 00001010

Bitwise AND -> both need to be 1 to be true
Bitwise OR -> one needs to be 1 to be true

ANDing is used to identify the host portion of an IPv4 address

Network address is the first address in a network: 192.168.10.0
^^^ can not be assigned to a host

Last Network address is a broadcast address
^^^ can not be assign to a host

Subnet Mask		32-bit Address			Prefix Length
255.0.0.0       11111111.00000000.00000000.00000000		/8
255.255.255.192 11111111.111111111.11111111.11000000		/26
		    ^8     ^8        ^8      ^2

Within each network there are 3 types of IP address
	- Subnet mask		255.255.255.0
	- Network address	192.168.10.0
	- Host addresses	192.168.10.1-254
	- Broadcast address	192.168.10.255

RFC - Request For Comments

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

For every network you want to make 2 to the power of (network amount) = the amount of bits you need to borrow

255.255.255.0 = /24
24 bits of network and 8 for host
11111111.11111111.11111111.00000000
^ this can only have 1 network (no subnets)

/25 = 255.255.255.128
25 bits for network 7 for host
11111111.11111111.11111111.10000000
^ this can have 2 networks (2 subnets)
192.168.1.128-254 = 126 hosts

to get number of hosts
2 to power network amount - 2

