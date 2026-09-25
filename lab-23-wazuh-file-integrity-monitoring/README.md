# Lab 23 - Wazuh File Integrity Monitoring Lab

## Objective

Validate **Wazuh File Integrity Monitoring (FIM)** on the monitored Windows endpoint by configuring a dedicated non-critical directory for real-time monitoring, creating and modifying a harmless test file, and verifying the resulting integrity-change event in the Wazuh Dashboard.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Wazuh server: `trioscyber`
- Windows endpoint: `Windows-Agent`
- Agent ID: `002`
- Endpoint IP: `10.10.20.30`
- Monitored path: `C:\Users\matthew\Documents\TriosFIMLab`
- Test file: `day23_test.txt`
- Monitoring mode: real time

## Laboratory Workflow

| Step | Activity | Result |
|---|---|---|
| 1 | Verify Wazuh server and Windows agent readiness | Server components active and `WazuhSvc` running |
| 2 | Create dedicated FIM laboratory directory | Safe non-critical path prepared |
| 3 | Back up `ossec.conf` | Original agent configuration preserved |
| 4 | Add the directory to Wazuh `syscheck` with `realtime="yes"` | Real-time FIM monitoring enabled |
| 5 | Restart the Wazuh Windows service | Updated configuration loaded |
| 6 | Create and modify `day23_test.txt` | Controlled integrity change generated |
| 7 | Review File Integrity Monitoring in Wazuh | File-change activity detected |
| 8 | Open the Wazuh event details | Source, path, rule and MITRE context validated |

## Real-Time FIM Configuration

The dedicated laboratory directory was added to the Wazuh agent `syscheck` configuration using real-time monitoring. Before modifying the configuration, the original `ossec.conf` file was backed up.

```xml
<directories realtime="yes">C:\Users\matthew\Documents\TriosFIMLab</directories>
```

The Wazuh Windows service was then restarted so the new FIM configuration could be loaded.

## Controlled File Modification

A harmless text file named `day23_test.txt` was created inside the monitored directory and then modified by appending additional content. This generated a controlled integrity change without modifying critical Windows files.

## Wazuh FIM Detection

The File Integrity Monitoring view registered activity for `Windows-Agent`, confirming that the configured directory was being monitored.

| Field | Observed Value |
|---|---|
| Agent ID | `002` |
| Agent name | `Windows-Agent` |
| Endpoint IP | `10.10.20.30` |
| Monitored file | `C:\Users\matthew\Documents\TriosFIMLab\day23_test.txt` |
| FIM event | `modified` |
| Syscheck mode | `realtime` |
| Decoder | `syscheck_integrity_changed` |
| Wazuh rule | `550` |
| Rule level | `7` |
| Rule description | `Integrity checksum changed` |
| MITRE ATT&CK | `T1565.001` - Stored Data Manipulation |
| MITRE tactic | Impact |

## Key Finding

The laboratory confirmed an end-to-end Wazuh FIM workflow: a monitored Windows directory was configured for real-time observation, a harmless file modification was generated, and Wazuh detected and classified the resulting integrity change with rule and MITRE ATT&CK context.

## Skills Demonstrated

- Wazuh File Integrity Monitoring configuration and real-time file-change detection
- File-integrity event validation and checksum-change analysis

## Tools and Platforms

- Wazuh File Integrity Monitoring (`syscheck`)
- Wazuh Windows agent and Dashboard
- Windows `ossec.conf`, `sc.exe` and `findstr`

## Full Report

[View PDF report](report.pdf)

> All file-integrity monitoring activity documented in this laboratory was performed in an isolated and authorized training environment using a dedicated non-critical test directory.
