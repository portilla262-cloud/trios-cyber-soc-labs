# Lab 30 - Final Practical SOC Investigation

## Objective

Perform an end-to-end SOC investigation using a safe, self-generated Windows service-creation scenario. The workflow covers telemetry readiness, event generation, Windows log investigation, Wazuh alert identification, initial triage, evidence correlation, MITRE ATT&CK mapping, cleanup, and final case disposition.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Monitored endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Controlled service: `TriosLab30`
- Windows event: System Event ID `7045`
- Wazuh rule: `61138`
- Wazuh rule level: `5`
- MITRE ATT&CK: `T1543.003` - Windows Service

## Investigation Workflow

| Step | Activity | Result |
|---|---|---|
| 1 | Verify endpoint telemetry in Wazuh | `Windows-Agent` actively reporting |
| 2 | Create controlled Windows service | `TriosLab30` created successfully |
| 3 | Investigate native Windows logs | Event ID `7045` confirmed |
| 4 | Identify Wazuh alert | Rule `61138`, Level `5` |
| 5 | Review detailed event evidence | Endpoint and service fields correlated |
| 6 | Perform initial triage | Activity validated as authorized lab behavior |
| 7 | Map behavior to MITRE ATT&CK | `T1543.003` - Windows Service |
| 8 | Remove the test service | `TriosLab30` deleted |
| 9 | Close the case | Benign / authorized laboratory activity |

## Telemetry Readiness

Before generating the test scenario, Wazuh Threat Hunting showed active telemetry from `Windows-Agent` (ID `002`). This confirmed that the endpoint-to-Wazuh collection path was functioning before the controlled activity was introduced.

## Controlled Service Creation

A harmless Windows service named `TriosLab30` was created with:

- Image path: `C:\Windows\System32\cmd.exe /c exit`
- Service account: `LocalSystem`
- Start type: Demand start

Windows returned a successful service-creation result, confirming that the controlled event had been generated.

## Windows Log Investigation

The Windows System log was queried for Service Control Manager Event ID `7045`.

| Field | Observed Value |
|---|---|
| Provider | Service Control Manager |
| Event ID | `7045` |
| Service name | `TriosLab30` |
| Image path | `C:\Windows\System32\cmd.exe /c exit` |
| Service account | `LocalSystem` |
| Start type | Demand start |
| Computer | `DESKTOP-VOJCDSO` |

The event confirmed that the controlled service was installed on the monitored endpoint.

## Wazuh Alert Identification

Wazuh Threat Hunting was filtered for the service name `TriosLab30`.

| Field | Observed Value |
|---|---|
| Agent | `Windows-Agent` / ID `002` |
| Service | `TriosLab30` |
| Rule ID | `61138` |
| Rule level | `5` |
| Description | `New Windows Service Created` |
| Alert time | Oct 1, 2026 @ 19:58:34.398 |

## Detailed Evidence and Initial Triage

Wazuh Document Details preserved the same service context observed in the Windows log.

| Triage Question | Observed Evidence | Assessment |
|---|---|---|
| What happened? | A new Windows service was installed | Service creation requires validation |
| Which asset? | `Windows-Agent` / ID `002` / `10.10.20.30` | Affected endpoint identified |
| Which service? | `TriosLab30` | Controlled service identified |
| Execution context | `cmd.exe /c exit` under `LocalSystem` | Privileged service context recorded |
| Alert classification | Rule `61138` / Level `5` | Wazuh classified the service-creation event |
| Was it authorized? | Yes - self-generated lab scenario | No evidence of unauthorized compromise |

## MITRE ATT&CK Mapping

Wazuh mapped the service-creation behavior to:

| Field | Observed Value |
|---|---|
| Technique | `T1543.003` - Windows Service |
| Tactics | Persistence, Privilege Escalation |
| Rule groups | `windows`, `windows_system` |

The mapping was supported by the service installation event, Service Control Manager provider, `LocalSystem` execution context, and service configuration.

## Closure and Escalation Recommendation

**Final disposition:** Close as benign / authorized laboratory activity.

The Windows and Wazuh evidence matched the self-generated test scenario, and no additional collected evidence indicated an unauthorized compromise.

For an equivalent unexplained event on a production endpoint, the case should remain open and be escalated for validation of:

- Service owner
- Service name
- Executable path
- Service account
- Start type
- Initiating change
- Surrounding endpoint activity

## Laboratory Cleanup

After evidence collection and analysis were completed, the `TriosLab30` service was removed from the Windows endpoint.

## Skills Demonstrated

- End-to-end SOC investigation lifecycle from telemetry collection to case closure
- Evidence-based triage, ATT&CK mapping and contextual disposition

## Tools and Platforms

This final laboratory consolidates tools already used throughout the previous practices, including Wazuh Threat Hunting, Windows System logs, `wevtutil`, `sc.exe`, Wazuh Document Details, and the Wazuh MITRE ATT&CK view.

## Full Report

[View PDF report](report.pdf)

> All activity documented in this laboratory was intentionally generated in an isolated and authorized training environment.
