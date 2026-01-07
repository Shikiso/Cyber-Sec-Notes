Read the help menu, decide what your looking for, scan.. (not hard)
Just know that NSE (NMAP Script Execution ) is a thing and that the
scripts can be found on the website or /usr/share/nmap/scripts/ 

## Common scans 
TCP Connect Scans `-sT`
SYN Scans `-sS`
UDP Scans `-sU`
TCP Null Scans `-sN`
TCP FIN Scans `-sF`
TCP Xmas Scans `-sX`

Use `-sn` if you are only interested in host-discovery without port-scanning.

## Stealth scan/TCP SYN scan
A stealth scan is just a tcp connection that doesn't fully
connect. Meaning the client sends the SYN request but once it
receives a reply from the server it drops the connection.
Because of this the TCP connection doesn't complete which
doesn't alert security systems at times. (Fuck around and find out ig)

This can bring down unstable services (apparently, i say fuck it).

## NULL, FIN & Xmas Scans #
All are uncommon so will go over quickly. Primarily used to be stealthy.
Usually used for firewall evasion.

NULL sends a TCP request with no flags, should get a RST reply
if the port is closed.

FIN scans work similar but sends the FIN flag and again expect
a RST reply is the port is closed.

Xmas scans send a malformed TCP packet and expects again RST 
reply is the port is closed.

## Firewall Evasion #
You can use `-Pn` to not ping the host treating the target as alive.
This will take ages tho.

If you're already on a local network NMAP can use ARP requests to find activity.

Some other switches are:
  `-f` Fragments the packets
  `--scan-delay {time}` adds delay
  `--badsum` generates invalid checksum for actions, most TCP/IP stacks will drops this 
  but firewalls may respond automatically.

Timing templates allow you to control how fast the scan runs. -T0-5, 5 being the most aggressive.
To avoid IDS alerts consider `-T0` or `-T1`.
Theses scan one port at a time and wait 5 min between each probe.

You can control the packet rate using `--min-rate {number}` or `--max-rate {number}`.

You can control probing parallelization using `--min-parrallelism={number}` or `--max-parrallelism={number}`

## TCP & UDP
#### SYN
You can send packets with the SYN flag set to a TCP port and if you get a SYN/ACK reply you know the port is open.

`nmap -PS21 127.0.0.1`

specific port  `-PS{port}`
port range `-PS{port}-{port}`
multiple ports `-PS{port},{port}`

#### ACK
This sends a packet with an ACK flag. You must be running NMAP as a privileged users. By default port 80 will be used but you can change the port same as SYN scan.

`namp -PA{port} -sn 127.0.0.1`

specific port  `-PA{port}`
port range `-PA{port}-{port}`
multiple ports `-PA{port},{port}`

### TCP Connect Scan
`nmap -sT 127.0.0.1`
Works by completing the TCP 3-way handshake.
Needs to be ran as sudo.
The connection is torn as soon as its state is confirmed by sending a RST/ACK.

### UDP
Sending a UDP packet to an open port will not lead to any expected reply. However if the port is closed we will get a ICMP port unreachable packet.

To send a normal UPD packet use `-sU`

To do a port scan on UDP:
`namp -PU{port} -sn 127.0.0.1`

specific port  `-PU{port}`
port range `-PU{port}-{port}`
multiple ports `-PU{port},{port}`

## Reverse-DNS lookup
By default NMAP uses reverse-DNS online hosts.
If you don't want to send such DNS queries you can use `-n`.
If you want to look up online hosts you can use `-R` to query the DNS server even for offline hosts. To use a specific DNS server you can add the `--dns-servers {server name}`

## ARP
An ARP scan is only possible if you are on the same subnet as the target system.
To perform a ARP scan using NMAP you want to use the `-PR` option

## Port States
1. **Open**: indicates that a service is listening on the specified port.
2. **Closed**: indicates that no service is listening on the specified port, although the port is accessible. By accessible, we mean that it is reachable and is not blocked by a firewall or other security appliances/programs.
3. **Filtered**: means that Nmap cannot determine if the port is open or closed because the port is not accessible. This state is usually due to a firewall preventing Nmap from reaching that port. Nmap’s packets may be blocked from reaching the port; alternatively, the responses are blocked from reaching Nmap’s host.
4. **Unfiltered**: means that Nmap cannot determine if the port is open or closed, although the port is accessible. This state is encountered when using an ACK scan `-sA`.
5. **Open|Filtered**: This means that Nmap cannot determine whether the port is open or filtered.
6. **Closed|Filtered**: This means that Nmap cannot decide whether a port is closed or filtered.

## TCP Flags
1. **URG**: Urgent flag indicates that the urgent pointer filed is significant. The urgent pointer indicates that the incoming data is urgent, and that a TCP segment with the URG flag set is processed immediately without consideration of having to wait on previously sent TCP segments.
2. **ACK**: Acknowledgement flag indicates that the acknowledgement number is significant. It is used to acknowledge the receipt of a TCP segment.
3. **PSH**: Push flag asking TCP to pass the data to the application promptly.
4. **RST**: Reset flag is used to reset the connection. Another device, such as a firewall, might send it to tear a TCP connection. This flag is also used when data is sent to a host and there is no service on the receiving end to answer.
5. **SYN**: Synchronize flag is used to initiate a TCP 3-way handshake and synchronize sequence numbers with the other host. The sequence number should be set randomly during TCP connection establishment.
6. **FIN**: The sender has no more data to send.