# Lab 13 - Correlation Rule Design and Manual Detection Testing

## Objective

Design and manually test a simple Splunk correlation rule for repeated failed authentication activity by combining event filtering, field extraction, grouping, threshold logic, and a short time window. Validate which user/source combinations trigger the rule and save the completed detection search for reuse.

## Environment

- Ubuntu Linux virtual machine
- Splunk Enterprise running locally on Ubuntu
- Splunk Web interface on TCP port `8000`
- Authentication-style events indexed in Splunk
- Users observed: `matthew`, `admin`, and `test`
- Source addresses observed: `10.10.10.20`, `10.10.10.30`, and `10.10.10.40`
- Authorized isolated laboratory environment

## Tools and Platforms

- Splunk Enterprise
- Splunk Search & Reporting
- Ubuntu Linux
- SPL correlation search
- SPL commands/functions including `rex`, `stats`, `eval`, `where`, `convert`, and `table`

## Key Activities

- Started Splunk Enterprise and verified Splunk Web availability on TCP port `8000`.
- Reviewed six indexed failed-authentication events with `result=FAILED`.
- Extracted the `user` and source-address fields and reviewed the events chronologically.
- Identified a repeated failed-authentication pattern for the same username and source IP.
- Defined a threshold-based detection condition requiring at least three failures from the same user and source IP within 60 seconds.
- Grouped failed events by user and source address in Splunk.
- Calculated the first and last failure timestamps and derived the correlation-window duration.
- Applied frequency and time-window conditions to determine whether each pattern triggered the detection logic.
- Validated the detection result against the sample authentication data.
- Saved the completed search as **Repeated Failed Authentication Detection** for later review.

## Detection Logic

The rule was configured with the following logic:

| Rule Element | Configured Value | Purpose |
|---|---|---|
| Event condition | `result=FAILED` | Restrict analysis to unsuccessful authentication events |
| Correlation key | Same `user` + same source IP | Link related authentication attempts |
| Threshold | `>= 3` failures | Require repeated activity before triggering |
| Time window | `<= 60` seconds | Restrict detection to a short burst of failures |
| Result | Trigger / no trigger | Distinguish matching activity from lower-frequency events |

## Key Findings

The rule returned one matching user/source combination:

| User | Source IP | Failures | Observed Window | Rule Result |
|---|---|---:|---:|---|
| `matthew` | `10.10.10.20` | 3 | 29 seconds | **Triggered** |
| `admin` | `10.10.10.30` | 2 | 10 seconds | Not triggered |
| `test` | `10.10.10.40` | 1 | Single event | Not triggered |

The `matthew / 10.10.10.20` pattern met both required conditions: three failed authentication events and a total correlation window below 60 seconds. The remaining patterns did not reach the configured threshold.

## Skills Demonstrated

- SIEM correlation rule design
- Threshold-based authentication detection
- User and source-IP event correlation
- Time-window based event analysis
- SPL field extraction and event grouping
- Detection-condition validation
- Authentication pattern analysis
- Saved correlation search/report creation
- Technical evidence collection and documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
