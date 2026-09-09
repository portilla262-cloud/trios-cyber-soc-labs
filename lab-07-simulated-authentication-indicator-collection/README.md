# Lab 7 – Simulated Authentication Scenario and Indicator Collection

## Objective

Simulate controlled local and remote authentication events inside an isolated laboratory environment and collect observable indicators that can be correlated during a basic SOC investigation.

## Environment

- Ubuntu Linux
- Windows
- Oracle VirtualBox
- Internal Network: `LAB-NET`
- Ubuntu endpoint: `10.10.10.10/24`
- Windows endpoint: `10.10.10.20`
- Authorized isolated laboratory environment

## Tools and Commands

- `journalctl`
- `grep`
- `su`
- `ssh`
- `whoami`
- `hostname`
- `date`
- `ip`
- OpenSSH / `sshd`
- PAM authentication logs
- Windows PowerShell

## Key Activities

- Verified that the Ubuntu endpoint was isolated from external networks.
- Collected baseline indicators including user, hostname, time, and endpoint IP address.
- Generated three controlled local authentication failures with `su`.
- Reviewed local authentication events using `journalctl`, PAM, and `FAILED SU` records.
- Prepared an authorized SSH service between the Windows and Ubuntu lab endpoints.
- Verified the Windows source endpoint and Ubuntu SSH destination.
- Generated controlled failed SSH authentication attempts from Windows.
- Correlated remote failed-login events with username, source IP, source port, timestamp, `sshd`, and PAM data.
- Built a concise event timeline from host and network indicators.

## Key Findings

The laboratory showed that authentication failures can be reconstructed from multiple observable fields, including:

- Username
- Hostname
- Endpoint IP
- Source IP
- Timestamp
- SSH service and destination port
- Remote source port
- `sshd` process information
- PAM authentication context
- Failed-password result
- Attempt count

The remote SSH scenario demonstrated how operating-system logs can preserve both endpoint and network context that can support alert triage and investigation.

## Skills Demonstrated

- Linux authentication log analysis
- SSH event investigation
- PAM log interpretation
- `journalctl` filtering
- Indicator collection
- Event correlation
- Authentication-failure analysis
- Basic SOC investigation workflow
- Timeline reconstruction
- Working safely in isolated lab environments

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
