DHCP is used to automate giving IP addresses to devices on a network. A DHCP server (which can be your router) provides your device with an IP address, subnet, default gateway and a DNS server.

DHCP is very useful when there is a large amount of devices connected to a network. The way I usually set this up is by having the first 10 addresses for any static device (my router, server, anything that needs a static IP) and the rest can be used by any device that wants them.

# Addressing Steps
1. **DHCP Discover**: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
2. **DHCP Offer**: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
3. **DHCP Request**: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
4. **DHCP Acknowledge**: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

![](/Images/dhcp_steps.png)

The address provides by the DHCP server are not permanent however. They are leased (provided) for a set amount of time.  When this time gets to a specific point such as 50% up the device will request a new lease. If this does not happen the IP address will be given to a requesting device.

# Some interesting things
In the DHCP packet exchange, we can notice the following:

- The client starts without any IP network configuration. It only has a MAC address. In the first and third packets, DHCP Discover and DHCP Request, the client searching for a DHCP server still has no IP network configuration and has not yet used the DHCP server’s offered IP address. Therefore, it sends packets from the IP address `0.0.0.0` to the broadcast IP address `255.255.255.255`.

- As for the link layer, in the first and third packets, the client sends to the broadcast MAC address, `ff:ff:ff:ff:ff:ff` (not shown in the output above). The DHCP server offers an available IP address along with the network configuration in the DHCP offer. It uses the client’s destination MAC address. (It used the proposed IP address in this example system.)