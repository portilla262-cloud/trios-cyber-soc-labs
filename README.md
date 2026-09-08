# TRIOS CYBER SOC Laboratory Practices

Hands-on cybersecurity laboratory activities completed during my SOC internship learning path with TRIOS CYBER.

This repository documents practical work in isolated and authorized lab environments, with a focus on networking, traffic analysis, service discovery, TCP behavior, endpoint baseline collection, and authentication log analysis.

## Laboratory Overview

| Lab | Topic | Main Tools | Key Skills |
|---|---|---|---|
| [Lab 1](./lab-01-isolated-virtual-network/) | Isolated Virtual Network Laboratory | VirtualBox, Ubuntu, Windows | Virtual networking, IPv4, ICMP, network isolation |
| [Lab 2](./lab-02-nmap-service-discovery/) | Nmap Scanning and Service Discovery | Nmap, Ubuntu, Metasploitable 2 | Host discovery, port scanning, service enumeration |
| [Lab 3](./lab-03-wireshark-protocol-analysis/) | Wireshark Traffic Capture and Protocol Analysis | Wireshark, Kali Linux, dig | DNS, TCP, HTTP, HTTPS/TLS, packet analysis |
| [Lab 4](./lab-04-tcp-handshake-analysis/) | TCP Connection Establishment and Teardown Analysis | Wireshark, Kali Linux, curl, Python HTTP server | TCP handshake, ports, FIN/ACK teardown |
| [Lab 5](./lab-05-endpoint-baseline/) | Endpoint Baseline Collection and System State Documentation | Kali Linux, Linux CLI tools | Process, service, socket, user and system-state baselining |
| [Lab 6](./lab-06-failed-authentication-log-analysis/) | Failed Authentication Attempts and Log Analysis | Kali Linux, journalctl, PAM, grep | Authentication log analysis, event correlation, failed-login investigation |

## Skills Demonstrated

- Network configuration and troubleshooting
- Safe host and service discovery
- Packet capture and protocol analysis
- TCP connection lifecycle analysis
- DNS and web traffic analysis
- Linux endpoint baseline collection
- Linux authentication log analysis
- Failed-login event correlation
- Technical documentation and evidence collection
- Working in isolated and authorized cybersecurity lab environments

## Tools and Platforms

- Oracle VirtualBox
- Ubuntu Linux
- Kali Linux
- Windows
- Wireshark
- Nmap
- Metasploitable 2
- `dig`, `curl`, `hostnamectl`, `ps`, `ss`, `systemctl`, `journalctl`, `grep`

## Reports

Each lab directory contains:

- A short README describing the objective, environment, activities and learning outcomes.
- The full PDF report with screenshots and technical evidence.

## Ethical and Safety Notice

All cybersecurity activities documented in this repository were performed in isolated laboratory environments or on systems explicitly authorized for training. No unauthorized systems were scanned, tested or accessed.

## Attribution

These reports were prepared as part of my SOC internship activities with TRIOS CYBER. This is a personal learning portfolio and is not an official TRIOS CYBER repository.
