# Lab 8 - Failed Authentication Event Triage and Disposition Analysis

## Objective

Review the failed-login evidence generated during Laboratory Practice 7 and perform a basic SOC triage to identify the affected asset, user, source, timeframe, likely cause, severity, and final event disposition.

## Environment

- Ubuntu Linux
- Windows
- Oracle VirtualBox
- Internal Network: `LAB-NET`
- Ubuntu endpoint: `matthew-VirtualBox` / `10.10.10.10/24`
- Windows source endpoint: `10.10.10.20`
- SSH service: TCP port `22`
- Authorized isolated laboratory environment

## Tools and Commands

- `journalctl`
- `grep`
- OpenSSH / `sshd`
- PAM authentication logs
- Ubuntu system logs

## Key Activities

- Reviewed the failed-login evidence generated during Laboratory Practice 7.
- Performed a focused review of SSH authentication logs for the original event window.
- Identified the affected Ubuntu asset, user account, SSH service, and Windows source endpoint.
- Reconstructed the authentication-event timeline from PAM and `sshd` records.
- Correlated the source IP, destination service, username, timestamps, and failed-password events.
- Assessed the most likely cause using the known laboratory context.
- Classified the event severity based on source, attempt count, authentication result, and environment.
- Determined whether the event should be closed, monitored, or escalated.
- Documented the final triage disposition and supporting evidence.

## Key Findings

The triage confirmed that the event matched the controlled SSH failed-login simulation performed during Laboratory Practice 7.

- Affected asset: `matthew-VirtualBox` (`10.10.10.10`)
- Affected user: `matthew`
- Source endpoint: Windows (`10.10.10.20`)
- Service: SSH / TCP `22`
- Failed password attempts: `3`
- Event timeframe: September 8, 2026, `22:57:29-22:57:41 (-05)`
- Successful unauthorized authentication: None observed
- Severity: Low
- Disposition: Close - Authorized Laboratory Activity

The evidence was consistent with an expected training event inside the isolated `LAB-NET` environment, so escalation was not required.

## Skills Demonstrated

- SOC alert and event triage
- Authentication log analysis
- SSH event investigation
- PAM log interpretation
- `journalctl` filtering
- Event correlation
- Timeline reconstruction
- Affected asset and user identification
- Severity assessment
- Event disposition decision-making
- Distinguishing expected activity from suspicious activity
- Working safely in isolated lab environments

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
