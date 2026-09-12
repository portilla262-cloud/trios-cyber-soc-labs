# Lab 10 - Authentication Log Extraction and Timeline Analysis

## Objective

Generate controlled SSH authentication activity between Windows and Ubuntu laboratory endpoints, extract successful and failed authentication records from the Ubuntu journal, and reconstruct a chronological authentication timeline using Linux command-line tools.

## Environment

- Oracle VirtualBox
- Ubuntu Linux endpoint
- Windows client endpoint
- VirtualBox Internal Network: `LAB-NET`
- Ubuntu address: `10.10.10.10/24`
- Windows source address: `10.10.10.20`
- OpenSSH / `sshd` on TCP port `22`
- Authorized isolated laboratory environment

## Tools and Commands

- Windows PowerShell
- OpenSSH / `sshd`
- `systemctl`
- `journalctl`
- `grep`
- `tail`
- `cat`

## Key Activities

- Configured Ubuntu and Windows virtual machines on the isolated `LAB-NET` internal network.
- Verified the Ubuntu endpoint identity, hostname, interface address, and system time before generating authentication activity.
- Confirmed that the SSH service was active and listening on TCP port `22`.
- Initiated an SSH connection from Windows PowerShell to `matthew@10.10.10.10`.
- Generated two intentionally failed password attempts followed by one successful authentication.
- Queried the Ubuntu SSH journal with `journalctl` and filtered for `Accepted password` and `Failed password` events using `grep`.
- Used `tail -n 10` to obtain a concise view of the most recent matching authentication records.
- Saved the filtered records to `authentication_time.txt` to preserve the relevant evidence for timeline reconstruction.
- Ordered the events chronologically and compared account, source IP, source port, service, protocol, timestamp, and authentication result.

## Key Findings

The extracted SSH authentication sequence contained three distinct events for the `matthew` account from source address `10.10.10.20`:

| Timestamp (-05) | Source IP | Result |
|---|---|---|
| 2026-09-12 12:39:38 | 10.10.10.20 | Failed |
| 2026-09-12 12:39:45 | 10.10.10.20 | Failed |
| 2026-09-12 12:39:49 | 10.10.10.20 | Successful |

All three records were associated with SSH/`sshd`, destination TCP port `22`, client source port `49673`, and SSH version 2. The sequence demonstrated how failed and successful authentication records can be correlated by shared fields and ordered to reconstruct the progression of a login session.

## Skills Demonstrated

- Linux authentication log extraction
- SSH authentication analysis
- Successful and failed login correlation
- `journalctl` log querying
- Command-line filtering with `grep` and `tail`
- Authentication timeline reconstruction
- Timestamp-based event correlation
- Source IP and port identification
- Evidence preservation in text files
- Linux service verification with `systemctl`
- SOC-oriented log review and technical documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
