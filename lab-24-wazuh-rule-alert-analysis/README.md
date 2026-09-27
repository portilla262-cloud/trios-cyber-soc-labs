# Lab 24 - Wazuh Rule and Alert Analysis

## Objective

Analyze three distinct Wazuh alerts from the monitored Windows endpoint and document the rule ID, alert level, description, source agent, timestamp, event context, and an appropriate first triage action for each alert.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Monitored endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Analysis interface: Wazuh Dashboard / Threat Hunting / Document Details

## Alerts Reviewed

| Alert | Rule / Level | Description |
|---|---|---|
| 1 | `61138` / Level `5` | New Windows Service Created |
| 2 | `550` / Level `7` | Integrity checksum changed |
| 3 | `503` / Level `3` | Wazuh agent started |

## Alert 1 - New Windows Service Created

The first alert corresponded to Windows Service Control Manager Event ID `7045` for service `TriosLab21`.

**Recommended first triage action:** Verify whether the service creation was authorized. Review the service name, executable path, service account, startup type, and change context before deciding whether escalation is required.

## Alert 2 - Integrity Checksum Changed

The second alert showed a real-time modification of:

`C:\Users\matthew\Documents\TriosFIMLab\day23_test.txt`

The event used Wazuh rule `550` at level `7` and preserved the modification state, changed attributes, file size before and after, integrity hashes, user information, and `syscheck.mode: realtime`.

**Recommended first triage action:** Confirm whether the file modification was authorized and review the affected path, timestamp, before/after hashes, changed attributes, and associated user.

## Alert 3 - Wazuh Agent Started

The third alert documented Wazuh agent startup activity using rule `503` at level `3`.

**Recommended first triage action:** Confirm whether the agent restart was expected, then review preceding stop, disconnection, service-control, or communication events for evidence of an operational problem or unauthorized interruption.

## Key Finding

The laboratory demonstrated how Wazuh rule metadata and event details can be used to establish context quickly and define an appropriate first-response action during SOC triage.

## Skills Demonstrated

- Wazuh rule and alert analysis with event-context interpretation
- First-response triage action definition from alert metadata

## Tools and Platforms

- Wazuh Dashboard - Threat Hunting / Document Details
- Wazuh Windows agent
- Windows System event telemetry
- Wazuh File Integrity Monitoring event data

## Full Report

[View PDF report](report.pdf)

> All analysis was performed in an isolated and authorized training environment.
