Logical Link Control takes the network protocol data, (IPv4 or IPv6 packet) and adds layer 2 control
information to help deliver the packer to the destination.
^ in short gives packet IP address to go to

Media Access Control provides data encapsulation
	- Frame delimiting: the framing process provides important delimiters to identity fields within a frame.
	- Addressing: provides source and destination addressing for transport
	- Error detection: includes a trailer used to detect transmission errors

Media Access Control method depends on:
	- Media sharing
	- Topology

Media Access Control responsibility it to provide the method to get the frame on and off the media

Half-Duplex - Only one device to send or receive at a time
Full-Duplex - Both devices transmit simultaneously

Ethernet - collision detection
Wireless - collision avoidance

Data Link protocol is responsible for NIC to NIC communications within the same network.
Allows upper layers access to physical layer
Encapsulates layer 3 packets into layer 2 frames

Data Link frames:
	- Header -> Frame Start -> Addressing -> Type -> Control
	- Data
	- Trailer -> Error Detection -> Frame Stop

Frame Start/Stop - used to identify the beginning and end limits of the frame
Addressing - Source and Destination
Type - The layer 3 protocol in the data field
Control - Identifies special flow control services such as quality of service (QoS)
Data - the data
Error Detection - Included after the data to form the trailer

Layer 2 addressing: Destination NIC, Source NIC, Source IP, Destination IP

WAN protocols:
	- Point to Point Protocol (PPP)
	- High Level Data Link Control (HDLC)
	- Frame Relay
	- Asynchronous Transfer Mode (ATM)
	- X.25

Data link layer protocols:
	- Ethernet
	- 802.11 Wireless
	- Point to Point Protocol (PPP)
	- High Level Data Link Control (HDLC)
	- Frame Relay

data -> switch -> looks for mac address in CAM table -> found mac -> send data -> not found -> send data to all except sender
