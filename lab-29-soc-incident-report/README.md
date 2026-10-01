# Lab 29 - SOC Incident Report

## Objective

Produce a concise SOC incident report from the repeated failed-authentication pattern previously investigated on the monitored Windows endpoint, consolidating the incident summary, affected asset, timeline, evidence, severity, actions taken, disposition, and recommendation.

## Incident Summary

A burst of five failed authentication events was observed against the same local Windows account within approximately 38 seconds.

| Field | Observed Value |
|---|---|
| Pattern | 5 repeated failed logons |
| Wazuh rule | `60122` / Level `5` |
| Windows event | Security Event ID `4625` |
| Target account | `matthew` |
| Final disposition | Authorized controlled activity |
| Final SOC severity | Low |
| Status | Closed - benign / authorized test |

## Affected Asset

| Field | Observed Value |
|---|---|
| Endpoint | `Windows-Agent` |
| Agent ID | `002` |
| IP address | `10.10.20.30` |
| Computer | `DESKTOP-VOJCDSO` |
| Target user | `matthew` |
| Source address | `127.0.0.1` |

## Incident Timeline

| Time | Event |
|---|---|
| ~00:40:47 | First matching Event ID `4625` recorded |
| 00:41:12.848 | Selected failed-logon alert reviewed in Wazuh |
| ~00:41:25 | Fifth matching failed-logon event recorded |

The five events formed one short repeated-failure sequence.

## Evidence Correlation

The report correlated Windows and Wazuh evidence:

- Windows Security Event ID `4625`
- `AUDIT_FAILURE`
- Five matching Wazuh alerts
- Source `127.0.0.1`
- Selected source port `49833`
- Network logon type `3`
- `NtLmSsp` / `NTLM`
- Wazuh rule `60122` at level `5`

## Severity and Analysis

The repeated failures were consistent with a **brute-force-style authentication pattern** and therefore justified investigation.

However, contextual review confirmed that the activity was intentionally generated as an authorized laboratory test. No evidence in the reviewed data indicated a real compromise.

```text
Detection severity: Wazuh Level 5
Final SOC severity: Low
Incident status: Closed - benign / authorized test
```

## Actions Taken

- Filtered Wazuh events by endpoint, Event ID `4625`, and target user
- Reviewed Windows Security event data
- Reviewed Wazuh Document Details
- Correlated the five records into one incident timeline
- Preserved supporting evidence for reporting
- Applied a contextual disposition

## Escalation and Recommendation

No escalation was required for the laboratory activity because it was authorized and locally generated.

For an equivalent unexplained production pattern, recommended triage would verify the target account, source IP, logon type, failure count and timing, and whether a successful authentication followed the failures. Continued or untrusted activity would justify deeper investigation and response according to organizational procedures.

## Skills Demonstrated

- SOC incident reporting and structured incident documentation
- Contextual severity, disposition, and escalation decision documentation

## Tools and Platforms

- Wazuh Threat Hunting / Document Details
- Windows Security Event ID `4625`
- Incident timeline and evidence correlation

## Full Report

[View PDF report](report.pdf)

> This report documents an authorized laboratory simulation and does not describe a real compromise.
