# Lab 12 - Authentication Event Search, Time Filtering, and Visualization with Splunk

## Objective

Use Splunk Enterprise to ingest authentication-style log data, search successful and failed authentication events, apply time-based filtering, summarize failed activity by username, create a visualization, and save the completed analysis as a reusable report.

## Environment

- Ubuntu Linux virtual machine
- Splunk Enterprise installed locally on Ubuntu
- Splunk Web interface on TCP port `8000`
- Host value: `matthew-VirtualBox`
- Sample log file: `sample_auth.log`
- Custom source type: `sample_auth`
- Authorized isolated laboratory environment

## Tools and Platforms

- Splunk Enterprise
- Splunk Search & Reporting
- Ubuntu Linux
- Firefox
- APT package manager
- SPL search commands including `rex` and `stats`
- `cat`

## Key Activities

- Installed Splunk Enterprise on the Ubuntu laboratory endpoint using the Linux AMD64 package and APT.
- Initialized Splunk, created administrator credentials, started the `splunkd` service, and verified access to Splunk Web on port `8000`.
- Prepared and reviewed the authentication-style file `sample_auth.log` before ingestion.
- Uploaded the log through Splunk's Add Data workflow.
- Assigned the custom source type `sample_auth` and host value `matthew-VirtualBox` before indexing.
- Used Search & Reporting to retrieve both `FAILED` and `SUCCESS` authentication outcomes.
- Applied a custom Date & Time Range to limit the investigation to the relevant event window.
- Extracted authentication fields with `rex` and summarized failed events with `stats count by user`.
- Converted the statistical results into a column chart for quick comparison by username.
- Saved the completed analysis as the report **Failed Authentication Events by User**.

## Key Findings

Seven authentication-style records were ingested and made searchable in Splunk. The dataset contained six failed authentication events and one successful event. Failed-event aggregation by username produced the following results:

| Username | Failed Events | Interpretation |
|---|---:|---|
| `matthew` | 3 | Highest failed-authentication count |
| `admin` | 2 | Second-highest failed-authentication count |
| `test` | 1 | Single failed-authentication event |

The analysis demonstrated a basic SIEM workflow in which raw authentication records were ingested, identified through a custom source type, searched, restricted to a relevant time window, aggregated by user, visualized, and preserved as a saved report.

## Skills Demonstrated

- Splunk Enterprise installation and basic initialization
- SIEM log ingestion and source-type configuration
- Authentication-event searching in Splunk
- SPL field extraction with `rex`
- Event aggregation with `stats`
- Time-based search filtering
- Failed-authentication frequency analysis
- Security-event visualization
- Saved search and report creation
- Basic SIEM investigation workflow
- Technical evidence collection and documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
