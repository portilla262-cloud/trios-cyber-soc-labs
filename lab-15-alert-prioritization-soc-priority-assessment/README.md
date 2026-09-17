# Lab 15 - Alert Prioritization and SOC Priority Assessment

## Objective

Prioritize five simulated security alerts using previously collected laboratory evidence and a qualitative SOC assessment based on asset criticality, repetition, user impact, and evidence quality. The activity focuses on assigning Low, Medium, or High priority according to operational context rather than event count alone.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Ubuntu Linux endpoint and SSH authentication evidence
- Splunk Enterprise correlation evidence
- Apache2 web access logs
- Windows Event Viewer / Service Control Manager evidence
- Spreadsheet-based prioritization matrix
- Simulated SOC alert scenarios derived from previously generated laboratory evidence

## Tools and Evidence Sources

- Splunk Enterprise
- Linux SSH authentication logs
- `journalctl`
- Apache2 access logs
- Windows Event Viewer
- Service Control Manager Event ID `7045`
- Spreadsheet used to compare alert-priority factors

## Priority Assessment Criteria

The five alerts were assessed using four factors:

| Factor | Low | Medium | High |
|---|---|---|---|
| Asset criticality | Disposable/test asset | Standard user or lab endpoint | Critical server or important business endpoint |
| Repetition | Single/isolated event | Several related events | Sustained or rapidly repeated activity |
| User impact | No observed impact | Potential or limited impact | Confirmed or significant access/impact |
| Evidence quality | Incomplete or weak evidence | Partially correlated evidence | Clear, timestamped and correlated evidence |

The final priority was determined by considering the factors together; repetition by itself did not automatically make an alert High priority.

## Simulated Alert Scenarios

| Alert | Scenario | Asset | Repetition | Impact | Evidence | Priority |
|---|---|---|---|---|---|---|
| `ALERT-01` | 3 failed SSH attempts from the same user/source in 29 seconds | Medium | High | Low | High | **Medium** |
| `ALERT-02` | Successful SSH login after repeated failures | Medium | Medium | High | High | **High** |
| `ALERT-03` | Repeated `/notfound.html` requests returning `404` | Low | High | Low | High | **Low** |
| `ALERT-04` | Repeated `GET` requests to authorized `/test.html` | Low | High | Low | High | **Low** |
| `ALERT-05` | Unexpected Windows service installation - Event `7045` | High | Low | Medium | High | **High** |

## Key Activities

- Reviewed five simulated SOC alert scenarios derived from existing laboratory evidence.
- Applied a qualitative prioritization matrix using asset criticality, repetition, user impact, and evidence quality.
- Assessed repeated failed SSH authentication activity validated through Splunk correlation evidence.
- Evaluated a failed-to-successful SSH authentication sequence as a higher-priority account-access scenario.
- Reviewed repeated Apache `404` responses and authorized `GET` requests in context instead of treating repetition alone as high severity.
- Assessed Windows Service Control Manager Event ID `7045` as a high-priority scenario when assumed to occur unexpectedly on an important endpoint.
- Compared the five scenarios and documented the rationale for Low, Medium, and High priority assignments.

## Alert Assessment Highlights

- **ALERT-01 - Medium:** three failed SSH attempts from `matthew` / `10.10.10.20` occurred within 29 seconds, but no successful unauthorized access was observed.
- **ALERT-02 - High:** two failed password attempts were followed by an accepted SSH password from the same source, creating a higher-impact account-access scenario.
- **ALERT-03 - Low:** repeated `404` responses affected only a local test service and produced no observed user or system impact.
- **ALERT-04 - Low:** repeated requests targeted an expected and authorized test resource, showing why repetition must be interpreted in context.
- **ALERT-05 - High:** an unexpected Windows service installation on an important endpoint can represent persistence or unauthorized system modification and therefore warrants higher analyst attention.

## Skills Demonstrated

- SOC alert prioritization and contextual triage
- Asset criticality and user-impact assessment
- Evidence-quality evaluation
- Multi-source security evidence comparison
- Priority justification using operational context
- Authentication, web-log, and Windows event evidence interpretation
- Spreadsheet-based alert assessment and documentation

## Full Report

[View PDF report](report.pdf)

> All alert scenarios were simulated from evidence generated in isolated and authorized laboratory environments. The assigned priorities represent analyst assessment before the activity is confirmed as authorized training traffic.
