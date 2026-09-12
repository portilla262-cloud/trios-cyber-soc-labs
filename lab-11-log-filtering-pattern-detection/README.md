# Lab 11 - Log Filtering and Pattern Detection

## Objective

Use Linux command-line text-processing tools to filter authentication-style log records, identify repeated usernames, source IP addresses, and failure messages, and summarize recurring patterns that could support initial SOC log analysis.

## Environment

- Ubuntu Linux laboratory endpoint
- Local authentication-style sample log
- Sample file: `sample_auth.log`
- Authorized isolated laboratory environment

## Tools and Commands

- `nano`
- `cat`
- `grep`
- `awk`
- `sort`

## Key Activities

- Created a seven-record authentication-style sample log containing timestamps, usernames, source IP addresses, results, and message fields.
- Verified the completed dataset with `cat`.
- Used `grep` with `result=FAILED` to isolate six unsuccessful authentication records.
- Filtered specifically for the repeated `Failed_password` message.
- Used `awk` and `sort` to extract and count repeated usernames.
- Applied the same counting workflow to source IP addresses.
- Counted failure-message values to identify the dominant failure pattern.
- Built a combined `grep`, `awk`, and `sort` pipeline to display failed records while retaining username, source IP, and message fields.
- Consolidated the results into a pattern-detection summary for rapid review.

## Key Findings

The seven-record sample contained six failed authentication results and one successful result. Repeated-value analysis produced the following dominant indicators:

| Pattern Type | Observed Value | Count | Interpretation |
|---|---|---:|---|
| Username | `matthew` | 4 | Most frequent username |
| Username | `admin` | 2 | Repeated account value |
| Source IP | `10.10.10.20` | 4 | Most frequent source address |
| Source IP | `10.10.10.30` | 2 | Repeated source address |
| Failure message | `Failed_password` | 5 | Dominant failure message |
| Failure message | `Invalid_user` | 1 | Single alternative failure message |

The exercise showed how simple Linux text-processing pipelines can reduce a small structured log dataset to the values that occur most frequently, making recurring authentication indicators easier to identify for follow-up investigation.

## Skills Demonstrated

- Linux command-line log analysis
- Log filtering with `grep`
- Structured field extraction with `awk`
- Frequency counting and sorting
- Repeated username detection
- Repeated source IP detection
- Failure-message pattern detection
- Authentication log pattern recognition
- Combined command-line analysis pipelines
- Rapid reduction of log data for SOC review
- Technical evidence collection and documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
