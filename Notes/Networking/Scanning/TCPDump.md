# Commands

| Command                 | Description                                              |
| ----------------------- | -------------------------------------------------------- |
| tcpdump -i  {Interface} | Listen on interface (Not required)                       |
| tcpdump -w {file.pcap}  | Output capture to file that can be analyzed by wireshark |
| tcpdump -r {file.pcap}  | Read capture from file                                   |
| tcpdump -c {num}        | Capture a set amount of packets                          |
| tcpdump -n              | Avoid making DNS lookups automatically                   |
| tcpdump -nn             | Same as -n but avoid port number lookups as well         |
| tcpdump -v              | Verbose display. Can be increased with -vv and -vvv      |
| tcpdump -q              | Quick and quite: brief packet information                |
| tcpdump -e              | Include MAC addresses                                    |
| tcpdump -A              | Print packets as ASCII encoding                          |
| tcpdump -xx             | Display packets in hexadecimal format                    |
| tcpdump -X              | Show packets in both hexadecimal and ASCII formats       |
# Filtering
| Argument           | Description                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------------- |
| host example.com   | Filter for specific hostname or ip address                                                                |
| src/dst            | Limits filter to source or destination (src host example.com)                                             |
| port {num}         | Filter for specific port                                                                                  |
| tcp/udp/icmp       | Filters for protocol (can use any)                                                                        |
| {command} \| wc    | Count lines                                                                                               |
| greater/less {num} | Filters packets that has a length greater or less                                                         |
| tcp[tcpflag]       | Filters for tcp flags, tcp-syn, tcp-ack, tcp-fin, tcp-rst, tcp-push. (tcpdump "tcp[tcpflags] == tcp-syn") |
# Logical Operators
- and
- or
- not
# Header Bytes
Using pcap-filter, Tcpdump allows you to refer to the contents of any byte in the header using the following syntax `proto[expr:size]`, where:
- `proto` refers to the protocol. For example, `arp`, `ether`, `icmp`, `ip`, `ip6`, `tcp`, and `udp` refer to ARP, Ethernet, ICMP, IPv4, IPv6, TCP, and UDP respectively.
- `expr` indicates the byte offset, where `0` refers to the first byte.
- `size` indicates the number of bytes that interest us, which can be one, two, or four. It is optional and is one by default.