# Lab 25 - Brute-Force Style Detection Simulation

## Objective

Simulate repeated authentication failures against a Windows laboratory account in a controlled manner, verify the corresponding Windows Security telemetry, confirm detection in Wazuh, count the failed attempts, and assess whether the observed pattern would require escalation.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Monitored endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Target account: `matthew`
- Windows Security Event ID: `4625`
- Controlled failed attempts: `5`

## Safety Check

Before generating repeated failures, the local account policy was reviewed with `net accounts`. The captured policy showed the account lockout threshold as **Never**, allowing the controlled test to proceed without intentionally triggering an account lockout.

## Controlled Authentication Failure Generation

Five authentication attempts were generated against the local `IPC$` resource using the laboratory account and a deliberately invalid password. Each attempt returned system error `1326`.

## Windows Security Event Verification

Windows recorded failed-logon telemetry under Event ID `4625`.

| Field | Observed Value |
|---|---|
| Target account | `matthew` |
| Source address | `127.0.0.1` |
| Logon type | `3` |
| Authentication | `NTLM` |
| Event ID | `4625` |

## Wazuh Detection and Attempt Count

Wazuh Threat Hunting displayed five matching failed-logon events from `Windows-Agent`.

| Metric | Observed Value |
|---|---|
| Failed attempts | `5` |
| Agent | `Windows-Agent` / `10.10.20.30` |
| Event ID | `4625` |
| Target account | `matthew` |

## Wazuh Rule Details

| Field | Observed Value |
|---|---|
| Rule ID | `60122` |
| Rule level | `5` |
| Description | `Logon Failure - Unknown user or bad password` |
| `rule.firedtimes` | `5` |
| Rule groups | `windows`, `windows_security`, `authentication_failed` |
| MITRE mapping | `T1531` - Account Access Removal |

## Escalation Assessment

The five failures against the same account in a short investigation window form a **brute-force-style pattern**.

Because the activity was intentionally generated from the local endpoint as an authorized laboratory simulation, no real incident escalation was required. An equivalent unexplained pattern in a production environment should be escalated for further investigation.

**Recommended first triage action:** Verify the target account, source IP, logon type, number and timing of failures, and determine whether a successful authentication occurred after the failed attempts.

## Skills Demonstrated

- Brute-force-style authentication pattern detection and repeated failed-logon analysis
- Failed-attempt counting, user-focused filtering and escalation assessment

## Tools and Platforms

- Wazuh Dashboard - Threat Hunting / Document Details
- Windows Security logs and Event ID `4625`
- Windows `net accounts` and `net use`
- Wazuh Windows agent

## Full Report

[View PDF report](report.pdf)

> All authentication failures documented in this laboratory were intentionally generated against the user's own laboratory account in an isolated and authorized training environment.
