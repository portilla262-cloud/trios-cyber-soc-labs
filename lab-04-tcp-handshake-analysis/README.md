# Lab 4 - TCP Connection Establishment and Teardown Analysis

## Objective

Capture and analyze the complete lifecycle of a TCP connection in a controlled local laboratory environment.

## Environment

- Kali Linux
- Wireshark
- Python local HTTP server
- `curl`
- Loopback interface (`127.0.0.1`)

## Activities

- Started an authorized local HTTP service on TCP port 80.
- Captured traffic from the loopback interface in Wireshark.
- Generated an HTTP connection with `curl`.
- Filtered the capture using `tcp.port == 80`.
- Identified the TCP three-way handshake.
- Reviewed client and server source/destination port roles.
- Observed HTTP request and response traffic.
- Identified the FIN/ACK sequence used to close the session.

## Connection Lifecycle Observed

1. SYN - client requests a connection.
2. SYN-ACK - server acknowledges and accepts.
3. ACK - client completes the three-way handshake.
4. HTTP request/response data is exchanged.
5. FIN/ACK packets close both sides of the connection.
6. Final ACK completes the teardown.

## Skills Demonstrated

- TCP/IP fundamentals
- Wireshark filtering
- Three-way handshake analysis
- Source and destination port analysis
- TCP connection teardown analysis

## Full Report

[View the complete PDF report](./report.pdf)
