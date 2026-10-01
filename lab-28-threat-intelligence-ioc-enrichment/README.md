# Lab 28 - Threat Intelligence / IOC Enrichment

## Objective

Investigate a safe training Indicator of Compromise (IOC) using **VirusTotal** for external reputation and metadata enrichment, then correlate the same indicator with internal Wazuh telemetry to evaluate how context changes analyst prioritization.

## IOC Scope

- IOC type: SHA-256
- Indicator: `275a021bbfb6489e54d471899f7db9d1663fc695ec2fe2a2c4538aabf651fd0f`
- Indicator identity: EICAR antivirus test file
- External reputation source: VirusTotal
- Monitored endpoint: `Windows-Agent` / ID `002`

## VirusTotal Reputation Search

The SHA-256 was searched directly in VirusTotal. The observed result was:

```text
63 / 65 detections
```

Multiple engines identified the indicator as **EICAR**, **EICAR-Test-File**, or similar test-file variants.

## IOC Metadata Enrichment

The VirusTotal Details view was used to preserve additional context, including:

- SHA-256 and other cryptographic hashes
- File type information
- EICAR identification
- File size (`68 B`)
- Submission and analysis history

## Contextual Interpretation

The high detection count initially raises suspicion, but the external context identifies EICAR as a harmless antivirus test string rather than a real virus.

Therefore, the raw reputation score alone was not treated as evidence of a real malware infection.

## Initial Wazuh Baseline Search

Before introducing a controlled training observation, the same SHA-256 was searched in Wazuh Threat Hunting for `Windows-Agent`.

```text
Initial result: No matching events
```

This established that the IOC had not previously been observed in the selected telemetry window.

## Controlled Training Observation

A controlled Windows Application event was created containing:

- `IOC_TEST`
- `EICAR`
- The selected SHA-256
- Source: `IOCTraining`

The event was created solely to validate the detection and correlation path.

## Wazuh IOC Detection

After the controlled observation, Wazuh returned one matching event.

| Field | Observed Value |
|---|---|
| Agent | `Windows-Agent` / ID `002` |
| Rule ID | `100500` |
| Rule level | `5` |
| Description | `Training IOC detected - EICAR SHA-256` |
| Hits | `1` |
| `data.indicator` | `EICAR` |
| `data.ioc_type` | `sha256` |
| `data.source` | `training` |
| Location | `synthetic-lab-event` |
| Rule groups | `ioc_training`, `threat_intelligence` |

## Analyst Prioritization

The laboratory demonstrated why IOC enrichment must combine **external reputation**, **internal telemetry**, and **operational context**.

A high reputation score can justify investigation, but the meaning of the indicator changes when it is identified as a known test artifact and when the internal match is a deliberately generated training event.

## Skills Demonstrated

- Threat intelligence and IOC enrichment using external reputation data
- External IOC reputation and internal SIEM telemetry correlation
- Context-based IOC prioritization and analyst interpretation

## Tools and Platforms

- VirusTotal
- Wazuh Threat Hunting / Document Details
- SHA-256 IOC analysis

## Full Report

[View PDF report](report.pdf)

> The IOC used in this laboratory was the EICAR antivirus test indicator and was handled only in an isolated and authorized training context.
