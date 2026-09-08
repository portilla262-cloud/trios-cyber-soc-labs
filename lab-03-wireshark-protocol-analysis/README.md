# Lab 3 - Wireshark Traffic Capture and Protocol Analysis

## Objective

Capture and analyze common network protocols from a Kali Linux laboratory system and compare the visibility of unencrypted and encrypted traffic.

## Environment

- Kali Linux
- Oracle VirtualBox
- NAT networking
- Wireshark
- `dig`

## Activities

- Configured Kali Linux with NAT networking and automatic IPv4 addressing.
- Verified Internet connectivity and DNS resolution.
- Prepared Wireshark and captured traffic from the active interface.
- Generated and analyzed DNS lookup traffic.
- Generated local HTTP traffic and inspected the readable HTTP request.
- Reviewed the TCP three-way handshake associated with the HTTP connection.
- Generated HTTPS traffic and analyzed TLS 1.3 packets.

## Key Findings

- DNS traffic used UDP port 53 and exposed the query and response information.
- TCP connection establishment followed the expected SYN, SYN-ACK and ACK sequence.
- HTTP traffic on port 80 exposed the application request in readable form.
- HTTPS traffic on port 443 used TLS 1.3, leaving application content encrypted while connection metadata remained observable.

## Skills Demonstrated

- Wireshark packet capture
- Display filtering
- DNS analysis
- TCP analysis
- HTTP vs HTTPS/TLS comparison
- Source, destination and port interpretation

## Full Report

[View the complete PDF report](./report.pdf)
