Using DHCP reduces complexity and amount of work necessary by using automatic IP configuration.
DHCP database - Dhcp.mdb

DHCP allocates leases to devices giving them an IP address for a specified amount of time.
DHCP lease generation:
	1. DHCP client broadcasts a DHCPDISCOVER packet
	2. DHCP server broadcasts a DHCPOFFER packet
	3. DHCP client broadcasts a DHCPREQUEST packet
	4. DHCP server broadcasts a DHCPACK packet

DHCP lease renewal:
	1. DHCP client sends a DHCPREQUEST packet
	2. DHCP server sends a DHCPACK packet
	3. If client fails to renew lease after 50% leave duration, DHCP lease renewal process begins again after 87.5%
		of the lease duration has expired.
	4. If the client fails to renew its lease after 87.5% of the lease as expired, the DHCP lease generation process
		starts over again with a DHCP client broadcasting DHCPDISCOVER 

How to deploy DHCP:
	1. Install and configure DHCP server role
	2. DHCP server authorization
	3. Allocate and manage IPv4 addresses
	4. Configure DHCP options

To allocate and manage IPv4 addresses with DHCP you must create a scope to define the network information.
A scope must contain:
	Range of IP addresses
	Subnet mask
	Lease duration
A scope might contain:
	Default gateway address
	DNS server and suffix
	Other network options
