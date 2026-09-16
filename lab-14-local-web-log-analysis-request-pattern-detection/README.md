# Lab 14 - Local Web Log Analysis and Request Pattern Detection

## Objective

Generate controlled HTTP activity against a local Apache web server, inspect the resulting access logs, identify key HTTP request fields, filter relevant records, and detect repeated request and status-code patterns using Linux command-line tools.

## Environment

- Ubuntu Linux virtual machine
- Apache2 web server running locally
- Firefox web browser
- Local HTTP traffic generated through `127.0.0.1`
- Apache access log: `/var/log/apache2/access.log`
- Custom test page: `/var/www/html/test.html`
- Authorized local laboratory environment

## Tools and Platforms

- Ubuntu Linux
- Apache2
- Firefox
- Apache access logs
- `systemctl`
- `tail`
- `grep`
- `awk`
- `sort`
- `uniq`

## Key Activities

- Installed Apache2 on the Ubuntu laboratory endpoint.
- Started the Apache service and verified that it was active and running.
- Created a local test page at `/var/www/html/test.html`.
- Cleared the Apache access log before generating the test traffic so the review would focus on the laboratory activity.
- Generated local HTTP requests from Firefox to the Apache default page, `/test.html`, and the intentionally missing `/notfound.html` path.
- Reviewed `/var/log/apache2/access.log` with `tail`.
- Identified client IP, HTTP method, requested path, status code, and browser User-Agent fields.
- Filtered `GET` requests with `grep`.
- Filtered HTTP `404` responses to isolate non-successful requests.
- Extracted request paths with `awk`, then sorted and counted them to identify repeated access patterns.
- Compared repeated requests to `/notfound.html` and reviewed the two `/test.html` responses.

## Observed Web Log Fields

| Field | Observed Value | Interpretation |
|---|---|---|
| Client IP | `127.0.0.1` | Local Firefox client |
| Request method | `GET` | HTTP method recorded by Apache |
| Main test path | `/test.html` | Custom laboratory page |
| Observed status codes | `200`, `304`, `404` | HTTP responses recorded in the access log |
| User-Agent | `Firefox/74.0` on Ubuntu Linux | Browser information stored in the request record |

## Request Pattern Findings

The request-path analysis identified the following repeated values:

| Request Path | Count | Observation |
|---|---:|---|
| `/notfound.html` | 9 | Most frequently repeated path; generated intentionally as a missing resource |
| `/icons/ubuntu-logo.png` | 3 | Repeated page-resource request |
| `/` | 3 | Apache default page requests |
| `/test.html` | 2 | Initial `200` response followed later by `304` |
| `/favicon.ico` | 2 | Browser favicon requests, including `404` responses |

The `404 Not Found` records were isolated as the non-successful status pattern in the sample traffic. Because `/notfound.html` was intentionally requested during the exercise, these records were expected laboratory activity rather than unexplained external traffic.

## Skills Demonstrated

- Apache web access-log analysis
- HTTP request-field identification
- HTTP status-code filtering and interpretation
- Request-path extraction and frequency analysis
- Repeated web-request pattern detection
- Linux command-line log filtering with `grep`, `awk`, `sort`, and `uniq`
- Web-log evidence review and technical documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
