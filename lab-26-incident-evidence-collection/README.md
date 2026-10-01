# Lab 26 - Incident Evidence Collection

## Objective

Collect and organize supporting evidence for a suspicious repeated-authentication pattern observed on the monitored Windows endpoint. The laboratory preserves endpoint identity, user information, timestamps, source details, Windows Security logs, Wazuh alert evidence, screenshots, and analyst notes in a structured incident directory.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Monitored endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Affected user: `matthew`
- Windows Security Event ID: `4625`
- Wazuh rule: `60122`
- Wazuh rule level: `5`
- Matching Wazuh records: `5`

## Incident Evidence Structure

A dedicated `Incident_DAY26` directory was created to separate evidence by source and purpose.

```text
Incident_DAY26/
├── 01_Endpoint/
├── 02_Logs/
├── 03_Wazuh/
├── 04_Screenshots/
└── 05_Notes/
```

This structure provides a clear handoff path for later review while keeping endpoint data, logs, Wazuh evidence, screenshots, and analyst notes organized.

## Endpoint and User Identification

Endpoint context was preserved using hostname, user, and IP configuration information.

| Field | Observed Value |
|---|---|
| Endpoint | `Windows-Agent` |
| Agent ID | `002` |
| Endpoint IP | `10.10.20.30` |
| Affected user | `matthew` |

## Windows Security Log Collection

The Windows Security log was queried for Event ID `4625` records targeting `matthew`.

Two evidence formats were retained:

- `Failed_Logons_4625.txt` - readable text export
- `Security_4625_matthew.evtx` - native Windows Event Log evidence

Keeping both formats preserves a human-readable copy for quick review and the native EVTX evidence for later event-log analysis.

## Incident Summary Notes

The incident notes consolidated the key evidence into one summary:

| Field | Observed Value |
|---|---|
| Pattern | Repeated failed authentication attempts |
| Endpoint | `Windows-Agent` |
| Agent ID | `002` |
| Agent IP | `10.10.20.30` |
| Target user | `matthew` |
| Windows Event ID | `4625` |
| Source address | `127.0.0.1` |
| Logon type | `3` |
| Authentication | `NTLM` |
| Wazuh rule | `60122` / Level `5` |
| Wazuh description | `Logon Failure - Unknown user or bad password` |
| Observed attempts | `5` |

## Wazuh Correlation and Timeline

Wazuh Threat Hunting was filtered to the Windows endpoint, Event ID `4625`, and target user `matthew`.

Five matching alerts were identified within a short time window, approximately:

```text
00:40:47 → 00:41:25
```

All five were classified under Wazuh rule `60122` at level `5`.

## Detailed Event Evidence

The selected Wazuh event preserved the authentication context required for incident review.

| Field | Observed Value |
|---|---|
| Agent | `Windows-Agent` / ID `002` |
| Endpoint IP | `10.10.20.30` |
| Source address | `127.0.0.1` |
| Selected source port | `49833` |
| Logon type | `3` |
| Authentication | `NtLmSsp` / `NTLM` |
| Target user | `matthew` |
| Windows channel | `Security` |
| Event ID | `4625` |
| Severity | `AUDIT_FAILURE` |
| Wazuh rule | `60122` |
| Rule level | `5` |
| Rule group | `authentication_failed` |
| Selected timestamp | Sep 27, 2026 @ 00:41:12.848 |

## Evidence Index

The screenshot evidence was numbered and stored with descriptive filenames. A `README_DAY26.txt` file was created as an incident index containing the pattern, affected endpoint, user, source, Windows event, Wazuh rule, attempt count, assessment, and evidence inventory.

## Validation Summary

| Requirement | Result |
|---|---|
| Affected endpoint | Verified |
| Affected user | Verified |
| Windows and Wazuh timestamps | Preserved |
| Source details | Preserved |
| Text log export | Collected |
| Native EVTX evidence | Collected |
| Five matching Wazuh alerts | Verified |
| Screenshots and incident structure | Completed |

## Skills Demonstrated

- Incident evidence collection and structured evidence organization
- Windows Security log export and native EVTX preservation
- Incident timeline, source-detail and authentication-evidence documentation

## Tools and Platforms

- Windows `wevtutil`
- Native Windows Event Log (`.evtx`) evidence
- Wazuh Threat Hunting / Document Details
- Windows command-line evidence collection (`hostname`, `whoami`, `ipconfig`, `tree`)

## Full Report

[View PDF report](report.pdf)

> All evidence documented in this laboratory was collected from an isolated and authorized training environment.
