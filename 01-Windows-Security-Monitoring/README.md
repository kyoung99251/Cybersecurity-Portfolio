Network Traffic Analysis with Wireshark

Project Overview

This project involved capturing and analyzing network traffic using Wireshark to understand how devices communicate across a network.

The investigation focused on Domain Name System (DNS) queries, Transmission Control Protocol (TCP) traffic, and the TCP three-way handshake.

The objective was to develop practical network analysis skills and understand how network protocols operate during normal communication.

Objectives

* Capture and inspect network traffic.
* Identify DNS queries and understand domain name resolution.
* Analyze TCP packets and connection behavior.
* Examine TCP flags, including SYN and ACK.
* Identify the stages of the TCP three-way handshake.
* Document findings and interpret packet-level evidence.

Tools and Environment

Tool	Purpose
Wireshark	Network traffic capture and analysis
Windows	Operating environment
Npcap	Packet capture support

1. DNS Traffic Analysis

Objective

Investigate DNS traffic and understand how domain names are resolved into IP addresses.

Investigation

Used the Wireshark display filter:

dns

The investigation included traffic associated with the domain:

example.com

Findings

* Identified DNS-related traffic during the capture.
* Investigated domain name resolution.
* Examined DNS traffic using Wireshark display filters.

Further Verification

The exact DNS transport protocol, response code, and packet count were not recorded.

2. TCP Traffic Analysis

Objective

Examine TCP communication between network devices and identify connection-establishment behavior.

Investigation

Used the following Wireshark display filters:

tcp

tcp.flags.syn == 1

These filters helped isolate TCP traffic and identify packets containing the SYN flag.

Observed Packet

Field	Observation
Packet Number	149
Timestamp	245.857245500
Source IP	10.0.0.59
Destination IP	142.251.35.110
Protocol	TCP
SYN Flag	Set
ACK Flag	Not Set

Analysis

Packet 149 was identified as an initial TCP SYN packet.

The SYN flag was set while the ACK flag was not set, indicating an initial TCP connection request.

3. TCP Three-Way Handshake

Objective

Identify and understand the three stages involved in establishing a TCP connection.

Stage 1: SYN — Synchronization

The client initiates communication by sending a TCP SYN packet to the destination.

Stage 2: SYN-ACK — Synchronization and Acknowledgment

The destination responds with a SYN-ACK packet, acknowledging the initial request and indicating readiness to establish the connection.

Stage 3: ACK — Acknowledgment

The client sends an ACK packet to acknowledge the response, completing the three-way handshake.

Investigation Results

All three handshake stages were identified in the Wireshark investigation.

Screenshots of the TCP handshake are included as supporting evidence.

Key Learning

The TCP three-way handshake establishes the initial connection between two devices before normal TCP data exchange begins.

Understanding these packets helps analysts investigate connection behavior and troubleshoot network communication.

Skills Demonstrated

* Network traffic analysis
* Wireshark packet inspection
* DNS traffic identification
* TCP protocol analysis
* TCP flag interpretation
* Network troubleshooting fundamentals
* Technical documentation
* Evidence-based investigation

Conclusion

This project provided hands-on experience capturing and analyzing network traffic using Wireshark.

The investigation demonstrated how DNS supports domain name resolution and how TCP establishes connections through the three-way handshake.

These foundational networking skills are relevant to Security Operations Center (SOC) analysis, network troubleshooting, and security monitoring.

Project Evidence

Screenshots documenting the DNS investigation, TCP packet analysis, and TCP three-way handshake are maintained in the Screenshots directory.

⸻

Project Type: Hands-on Cybersecurity Lab

Focus Area: Network Security / Blue Team Fundamentals

Tool: Wireshark