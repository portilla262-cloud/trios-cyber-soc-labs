# Lab 27 - MITRE ATT&CK Mapping Lab

## Objective

Map a simulated Windows service-creation behavior to the most relevant **MITRE ATT&CK** technique using Wazuh ATT&CK telemetry and the corresponding Windows EventChannel evidence.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Windows event: System Event ID `7045`
- Wazuh rule: `61138` / Level `5`
- Mapped technique: `T1543.003` - Windows Service

## Behavior Selected for Mapping

The selected behavior was the creation of the simulated Windows service `TriosLab21` on the monitored endpoint.

| Field | Observed Value |
|---|---|
| Service name | `TriosLab21` |
| Image path | `C:\Windows\System32\cmd.exe /c exit` |
| Service account | `LocalSystem` |
| Start type | Demand start |
| Windows event | System / Event ID `7045` |

## MITRE ATT&CK Activity Overview

The Wazuh MITRE ATT&CK view showed **Windows Service** among the techniques observed for `Windows-Agent` and included **Persistence** and **Privilege Escalation** among the active tactics.

## Technique-Specific Filtering

The Wazuh Events view was filtered using:

```text
rule.mitre.id:"T1543.003"
```

Four matching records were returned for `Windows-Agent`. Each record was classified as **New Windows Service Created** under Wazuh rule `61138` at level `5`.

## Mapping Evidence

The selected Wazuh document preserved both the Windows service details and the ATT&CK correlation fields.

| Field | Observed Value |
|---|---|
| Endpoint | `Windows-Agent` / ID `002` / `10.10.20.30` |
| Windows Event ID | `7045` |
| Provider | Service Control Manager |
| Wazuh rule | `61138` / Level `5` |
| Description | `New Windows Service Created` |
| ATT&CK technique | `T1543.003` - Windows Service |
| ATT&CK tactics | Persistence / Privilege Escalation |

## Mapping Rationale

The mapping to `T1543.003 - Windows Service` is supported directly by the creation of `TriosLab21`, Windows Event ID `7045`, the Service Control Manager provider, the service executable path, and the `LocalSystem` service context.

```text
T1543.003 - Windows Service | Persistence | Privilege Escalation
```

## Skills Demonstrated

- Evidence-based MITRE ATT&CK technique mapping
- ATT&CK tactic and technique validation using Wazuh and Windows event evidence

## Tools and Platforms

- Wazuh MITRE ATT&CK dashboard
- Wazuh Threat Hunting / Document Details
- Windows System Event ID `7045`

## Full Report

[View PDF report](report.pdf)

> All behavior analyzed in this laboratory was generated in an isolated and authorized training environment.
