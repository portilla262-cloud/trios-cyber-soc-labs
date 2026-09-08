# Lab 5 - Endpoint Baseline Collection and System State Documentation

## Objective

Create a repeatable baseline of a Kali Linux endpoint so future investigations can compare the current system state against a known reference.

## Environment

- Kali Linux
- Oracle VirtualBox
- Linux command-line utilities

## Baseline Data Collected

| Baseline Item | Command / Method | Saved Output |
|---|---|---|
| Hostname and system identity | `hostnamectl` | `hostname.txt` |
| Current user and account identity | `whoami`, `id` | `current_user.txt` |
| Running processes | `ps aux` | `running_processes.txt` |
| Active listening network sockets | `ss` | `active_connections.txt` |
| TCP connection state | `ss -tn` | `tcp_connections.txt` |
| Running services | `systemctl --type=service --state=running` | `running_services.txt` |
| Enabled startup services | `systemctl list-unit-files --type=service --state=enabled` | `startup_services.txt` |
| Consolidated baseline | Combined command output | `baseline_lab5.txt` |

## Activities

- Created a dedicated workspace for baseline evidence.
- Recorded endpoint identity and current-user information.
- Captured the running process state.
- Recorded active listening sockets and TCP sessions.
- Collected running and enabled services.
- Consolidated the baseline information into a single reference artifact.

## Security Relevance

A baseline can support SOC investigations by making it easier to identify changes such as:

- New or unexpected processes
- Unexpected listening ports
- New TCP sessions
- Service-state changes
- New automatically enabled services

## Skills Demonstrated

- Linux endpoint inspection
- Process and service analysis
- Network socket review
- Baseline creation
- SOC evidence collection and documentation

## Full Report

[View the complete PDF report](./report.pdf)
