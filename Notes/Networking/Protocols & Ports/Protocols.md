# Hybrid Protocol
A hybrid protocol is a protocol that combines features or techniques from two or more different types of protocols, taking advances of each ones strength.
# Internet Control Message Protocol (ICMP)

- Usually blocked due to security reasons
- Available for IPv4 (ICMPv4) and IPv6 (ICMPv6)
- Used to test reachability of a host

ICMPv6 has 4 new protocols as part of the Neighbor Discovery Protocol (ND or NDP)
Messaging between an IPv6 router and host:
	Router Solicitation (RS) message - IPv6-enable router will send RA message in response to RS message
	Router Advertisement (RA) message - Sent every 200s to provide addressing info to IPv6-enables hosts.
Between IPv6 devices:
	Neighbor Solicitation (NS) message - To ensure a IPv6 address is unique the device will send a NS message with its own address as the target address. If another device has the address a NA message will be sent.
	Neighbor Advertisement (NA) message - Used to find out MAC address when IPv6 unicast address is known

If a host/gateway receives a packet that it cant deliver. It uses an
ICMP Destination Unreachable message to notify the source that service/destination
is unavailable.

Destination Unreachable codes for ICMPv4s:
	0 - Net unreachable
	1 - Host unreachable
	2 - Protocol unreachable
	3 - Port unreachable

Destination Unreachable codes for ICMPv6:
	0 - No route to destination
	1 - Communication with the destination is administratively prohibited (e.g., firewall)
	2 - Beyond scope of the source address
	3 - Address unreachable
	4 - Port unreachable


# HTTP/s:
- When a URL is typed into a web browser the web browser establishes a connection to a web service
- When a client sends request to a web server, HTTP specifies the message type for the communication
- GET: Request Data
- POST: Uploads data files
- PUT: Uploads resources

# Email:
## SMTP:
- Require header and body message
- When client sends email client SMTP is connected with server SMTP on port 25.
- After the connection is made the client attempts to send email to the server
- When the server receives the message it either places the message in a local account or forwards the message to another mail server for delivery
- If destination server unavailable SMTP spools messages to be sent at a later time.
- The server checks this queue and attempts to send again
- If unavailable to send after a predetermined time it is returned as undelivered
## POP:
- Application used to retrieve mail from mail server
- When mail is downloaded from the server to the client it is deleted from the server
- server starts POP service by listening on TCP port 110 for client connection requests
- When connection is established the POP sends a greeting and the client exchanges commands and responses
- POP does not store messages so it can not have backups
## IMAP:
- Method to retrieve email messages
- Copies of messages are downloaded to client application

### Notes
SMTP functions between the senders device and the receivers mailbox.
	- Sends email from senders device to receivers mailbox
POP3 functions between the receiver and receivers mail server
	- Retrieves and organizes emails from the receivers mail server to the receivers device

# DNS (Dynamic Name System)
DNS used to convert domain names into IP addresses.
DNS client service on Win also stores previously resolved names in mem (ipconfig /displaydns)
To get IP address:
	- Client will make request for website
	- If IP is not known client will ask closest DNS server
	- IF DNS server doesn't know it will ask the ROOT DNS
	- Will loop asking DNS servers until IP is found
	- Will then make request to IP NOT domain


A - An end device IPv4 address
NS - An authoritative name server
AAAA - An end device IPv6 address (pronounced quad-A)
MX - A mail exchange record

"nslookup" allows users to manually query the name servers to find a host

# DHCP (Dynamic Host Configuration Protocol)
- Automates the assigned of IPv4 addresses, subnets and gateways
- The alternative is static addressing
- When a host connects to a network the DHCP is contacted and a address is requested
- DHCP server chooses an address from a configured range and leases it to the host
- Lease period is the amount of time a host can have an IP address
- When the lease expires the DHCP server gets a DHCPRELEASE message and the address is returned
[(Learn more)](Notes/Networking/Protocols%20&%20Ports/DHCP.md)

# FTP (File Transfer Protocol)
- Used to transfer files
- Allows transfer between server and client
- Port 21 for control traffic
- Port 20 to transfer data

# SMB (Server Message Block)
- Client/Server file sharing protocol
- 3 functions
	- Start, authenticate and terminate sessions
	- Control file and printer access
	- Allow an application to send or receive messages to or from another device

- (Uses TCP)
- Server Message Block Protocol (SMB) is a cliendd t-server communication protocol used for sharing access to file, printers, serial ports, etc on a network.

- Is a response-request protocol, meaning it can transmit multiple messages between the client and server to establish a connection.

# TLS (Transport Layer Security)
A cryptographic protocol that secures communication over networks.
It ensures data sent is encrypted, authentication and is integrity protected.

## Stages
### Handshake
1. **Client Hello** – The client sends supported TLS versions, encryption algorithms, and a random value.
2. **Server Hello** – The server chooses compatible encryption settings and sends its **digital certificate** (which includes its public key).
3. **Certificate Verification** – The client checks the certificate’s validity via a trusted Certificate Authority (CA).
4. **Key Exchange** – Both sides use the public key or Diffie-Hellman methods to securely agree on a **session key**.
5. **Handshake Complete** – Now both sides share the same secret key but no one else knows it.
### Data Transfer
Once the handshake is done:
- All communication is **encrypted** using symmetric encryption (fast and efficient).
- Each message includes a **Message Authentication Code (MAC)** to ensure integrity.    
- If any tampering or corruption occurs, the connection is terminated.

