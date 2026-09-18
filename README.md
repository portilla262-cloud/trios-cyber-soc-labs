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
| [Lab 7](./lab-07-simulated-authentication-indicator-collection/) | Simulated Authentication Scenario and Indicator Collection | Ubuntu, Windows, SSH, journalctl, PAM | SSH log analysis, indicator collection, event correlation, timeline reconstruction |
| [Lab 8](./lab-08-failed-authentication-event-triage-disposition-analysis/) | Failed Authentication Event Triage and Disposition Analysis | Ubuntu, journalctl, SSH/sshd, PAM | SOC triage, severity assessment, event disposition, evidence correlation |
| [Lab 9](./lab-09-windows-event-viewer-log-inspection-soc-relevance-analysis/) | Windows Event Viewer Log Inspection and SOC Relevance Analysis | Windows Event Viewer, Security/System/Application logs | Windows event log analysis, event filtering, authentication analysis, SOC relevance assessment |
| [Lab 10](./lab-10-authentication-log-extraction-timeline-analysis/) | Authentication Log Extraction and Timeline Analysis | Ubuntu, Windows PowerShell, SSH, journalctl, grep, tail | Authentication log extraction, SSH event correlation, timeline reconstruction, evidence preservation |
| [Lab 11](./lab-11-log-filtering-pattern-detection/) | Log Filtering and Pattern Detection | Ubuntu, grep, awk, sort | Log filtering, field extraction, frequency analysis, repeated-indicator detection |
| [Lab 12](./lab-12-splunk-authentication-event-search-time-filtering-visualization/) | Authentication Event Search, Time Filtering, and Visualization with Splunk | Splunk Enterprise, Ubuntu, Search & Reporting, SPL | SIEM log ingestion, authentication-event search, time filtering, aggregation, visualization and reporting |
| [Lab 13](./lab-13-correlation-rule-design-manual-detection-testing/) | Correlation Rule Design and Manual Detection Testing | Splunk Enterprise, Search & Reporting, SPL | SIEM correlation-rule design, threshold detection, user/source correlation, time-window analysis |
| [Lab 14](./lab-14-local-web-log-analysis-request-pattern-detection/) | Local Web Log Analysis and Request Pattern Detection | Apache2, Ubuntu, Firefox, grep, awk | Web access-log analysis, HTTP field identification, status-code filtering, repeated-request detection |
| [Lab 15](./lab-15-alert-prioritization-soc-priority-assessment/) | Alert Prioritization and SOC Priority Assessment | Splunk, SSH logs, Apache access logs, Windows Event Viewer, spreadsheet | Alert prioritization, asset criticality, impact assessment, evidence-quality evaluation |
| [Lab 16](./lab-16-wazuh-server-vm-deployment-preparation-network-planning/) | Wazuh Server VM Deployment Preparation and Network Planning | Oracle VirtualBox, Ubuntu Server, Linux CLI | Wazuh deployment preparation, resource validation, network planning, pre-installation readiness assessment |

## Skills Demonstrated

- Network configuration and troubleshooting
- Host and service discovery
- Packet capture and protocol analysis
- TCP connection lifecycle analysis
- DNS and web traffic analysis
- Linux endpoint baseline collection
- Linux authentication log analysis
- SSH authentication investigation
- Windows Event Viewer log analysis
- Windows authentication and privileged-logon analysis
- Windows service-installation event analysis
- SOC event triage and evidence correlation
- Affected asset, user and source identification
- Severity assessment and event disposition
- Event filtering and SOC relevance assessment
- Authentication event correlation and timeline reconstruction
- Source IP, port and authentication-field analysis
- Linux command-line log analysis
- Log filtering and structured field extraction with `grep` and `awk`
- Frequency analysis and security log pattern detection
- Indicator collection and evidence preservation
- Technical documentation and evidence collection
- Splunk SIEM log ingestion and source-type configuration
- SPL authentication-event searching and time filtering
- Event aggregation, visualization and saved-report creation
- SIEM correlation-rule design and threshold-based detection
- User/source correlation and time-window analysis
- Detection validation and reusable correlation searches
- Apache web access-log analysis and HTTP request-pattern detection
- HTTP status-code and request-path analysis
- SOC alert prioritization using asset criticality, repetition, user impact and evidence quality
- Multi-source alert assessment and priority justification
- Wazuh server deployment preparation and pre-installation readiness assessment
- Linux server resource, storage and connectivity validation
- SIEM infrastructure and network planning

## Tools and Platforms

- Oracle VirtualBox
- Ubuntu Linux
- Kali Linux
- Windows
- Wireshark
- Nmap
- Metasploitable 2
- `dig`, `curl`, `hostnamectl`, `ps`, `ss`, `systemctl`, `journalctl`, `grep`
- Windows Event Viewer (`eventvwr.msc`)
- Windows Security, System and Application logs
- Splunk Enterprise
- Splunk Search & Reporting
- SPL commands including `rex`, `stats` `rex`, `stats`, `eval`, `where`, `convert` and `table`
- Apache2 and Apache access logs (`/var/log/apache2/access.log`)
- Firefox
- Ubuntu Server 24.04 LTS
- hostname, uname, ip, ping, free, nproc, lsblk, df, sudo

## Reports

Each lab directory contains:

- A short README describing the objective, environment, activities and learning outcomes.
- The full PDF report with screenshots and technical evidence.

## Ethical and Safety Notice

All cybersecurity activities documented in this repository were performed in isolated laboratory environments or on systems explicitly authorized for training. No unauthorized systems were scanned, tested or accessed.

## Attribution

These reports were prepared as part of my SOC internship activities with TRIOS CYBER. This is a personal learning portfolio and is not an official TRIOS CYBER repository.
