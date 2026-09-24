# Lab 21 - Endpoint Event Collection Test and Wazuh Telemetry Verification

## Objective

Generate a controlled Windows endpoint event and verify the complete telemetry path from the local Windows System log to the centralized Wazuh platform.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Wazuh server: `trioscyber` / `10.10.20.10`
- Windows endpoint: `Windows-Agent` / `10.10.20.30`
- Wazuh agent ID: `002`
- Test activity: temporary Windows service `TriosLab21`
- Windows event investigated: Event ID `7045`

## Laboratory Workflow

The practice validated the event from its origin on the Windows endpoint through its reception and classification in Wazuh.

| Step | Activity | Result |
|---|---|---|
| 1 | Verify Wazuh server and Windows agent services | Server components active and `WazuhSvc` running |
| 2 | Create temporary service `TriosLab21` | Controlled service-change activity generated |
| 3 | Query the local Windows System log | Event ID `7045` confirmed locally |
| 4 | Validate the Wazuh event document | Source endpoint and event fields matched |
| 5 | Review Wazuh rule and MITRE context | Rule `61138`, level `5`, MITRE `T1543.003` |
| 6 | Confirm event in Threat Hunting | Telemetry searchable in Wazuh |
| 7 | Delete the temporary service | Endpoint returned to its prior lab state |

## Controlled Endpoint Activity

A temporary Windows service named `TriosLab21` was created for the collection test. The local Windows System log recorded the expected **Service Control Manager Event ID 7045**, confirming that the endpoint produced the intended telemetry before Wazuh correlation.

## Wazuh Telemetry Verification

Wazuh received the corresponding event from `Windows-Agent` and preserved the endpoint and event context.

| Field | Observed Value |
|---|---|
| Agent ID | `002` |
| Agent name | `Windows-Agent` |
| Endpoint IP | `10.10.20.30` |
| Windows channel | `System` |
| Windows Event ID | `7045` |
| Provider | Service Control Manager |
| Service name | `TriosLab21` |
| Wazuh rule | `61138` |
| Rule level | `5` |
| Rule description | `New Windows Service Created` |
| MITRE ATT&CK | `T1543.003` - Windows Service |
| MITRE tactics | Persistence / Privilege Escalation |

## Threat Hunting Validation

The event was confirmed as searchable in Wazuh Threat Hunting using the monitored Windows endpoint and Event ID `7045`. The current laboratory event appeared under the Wazuh detection **New Windows Service Created**.

## Laboratory Cleanup

After validation, the temporary `TriosLab21` service was removed so the Windows endpoint was returned to its previous laboratory state.

## Skills Demonstrated

- Wazuh Threat Hunting and endpoint telemetry investigation
- Wazuh rule correlation and source endpoint validation
- MITRE ATT&CK mapping from Windows endpoint telemetry

## Tools and Platforms

- Wazuh Dashboard - Threat Hunting / Events
- Wazuh Windows agent
- Windows System event logs
- Windows 10 endpoint

## Full Report

[View PDF report](report.pdf)

> All activity documented in this laboratory was performed in an isolated and authorized training environment.
