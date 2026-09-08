# Lab 6 – Failed Authentication Attempts and Log Analysis

## Objective

Generate controlled failed authentication events in a local Kali Linux laboratory environment and analyze the resulting operating-system logs.

## Environment

- Kali Linux
- Local laboratory account
- Authorized virtual environment

## Tools and Commands

- `journalctl`
- PAM logs
- `su`
- `whoami`
- `grep`

## Key Activities

- Verified the active laboratory account.
- Generated three controlled failed authentication attempts.
- Located authentication failures using `journalctl`.
- Identified PAM authentication failure and `FAILED SU` events.
- Reviewed account, UID, terminal session, hostname, and timestamps.
- Correlated command activity with operating-system log events.
- Evaluated the security relevance of failed authentication records.

## Key Findings

The operating system successfully recorded the controlled authentication failures and preserved useful investigation context, including:

- Account
- UID
- Hostname
- Terminal session
- Authentication module
- Timestamp
- Authentication result

These fields can help SOC analysts distinguish expected administrative activity from suspicious authentication attempts.

## Skills Demonstrated

- Linux log analysis
- Authentication event investigation
- `journalctl` filtering
- PAM log interpretation
- Event correlation
- SOC alert investigation fundamentals

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an authorized local laboratory environment.
