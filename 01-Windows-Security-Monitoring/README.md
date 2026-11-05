TCP Traffic Analysis

Objective

Analyze TCP traffic using Wireshark and identify the TCP three-way handshake.

Tools Used

* Wireshark
* Windows 11

Observed TCP Packet

Field	Observation
Packet Number	149
Timestamp	245.857245500
Source IP	10.0.0.59
Destination IP	142.251.35.110
Protocol	TCP
SYN Flag	Set
ACK Flag	Not set

Analysis

Packet 149 was identified as an initial TCP SYN packet. The SYN flag was set while the ACK flag was not set, indicating that the source device initiated a TCP connection request.

Next Investigation

Identify the corresponding SYN-ACK response and final ACK packet to verify the TCP three-way handshake.

Key Learning

The TCP three-way handshake establishes a connection through three steps:

1. SYN – Client initiates the connection.
2. SYN-ACK – Server acknowledges and responds.
3. ACK – Client acknowledges the server’s response.
