# Lab 17 - Wazuh All-in-One Installation and Dashboard Verification

## Objective

Deploy Wazuh in all-in-one mode on the prepared Ubuntu Server virtual machine, verify that the core Wazuh services are running, and confirm secure browser access to the Wazuh dashboard through a local SSH tunnel from the Windows host.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS (x86_64)
- Dedicated Wazuh server VM
- 8192 MB RAM
- 4 vCPU
- 100 GB virtual disk
- VirtualBox NAT networking
- Windows host used for browser access and SSH tunneling

## Wazuh All-in-One Components

The installation assistant deployed the main Wazuh components on the same Ubuntu Server:

- Wazuh manager
- Wazuh indexer
- Wazuh dashboard
- Filebeat

## Key Activities

- Increased the Wazuh server VM resources to 8192 MB RAM and 4 vCPU before deployment.
- Ran the Wazuh installation assistant in all-in-one mode.
- Completed Wazuh indexer configuration and cluster initialization.
- Installed and started the Wazuh manager.
- Installed and started Filebeat.
- Installed and initialized the Wazuh dashboard.
- Verified the four main services with `systemctl is-active`.
- Created an SSH local port-forwarding tunnel from the Windows host to the Ubuntu Server.
- Accessed the Wazuh HTTPS login interface through the forwarded local port.
- Authenticated to the dashboard and verified that the Wazuh Overview page loaded successfully.
- Confirmed that no endpoint agents were registered at this stage, which was outside the scope of the laboratory.

## Core Service Verification

| Component | Verification | Result |
|---|---|---|
| Wazuh manager | `systemctl is-active wazuh-manager` | Active |
| Wazuh indexer | `systemctl is-active wazuh-indexer` | Active |
| Wazuh dashboard | `systemctl is-active wazuh-dashboard` | Active |
| Filebeat | `systemctl is-active filebeat` | Active |

## SSH Tunnel Configuration

Because the Ubuntu Server remained behind VirtualBox NAT, browser access was provided through local SSH port forwarding rather than exposing the dashboard externally.

| Tunnel Element | Observed Value |
|---|---|
| Windows browser endpoint | `https://127.0.0.1:8443` |
| SSH connection | `matthew@127.0.0.1` on host port `2222` |
| Forwarded destination | `127.0.0.1:443` on the Ubuntu Server |
| Local forwarding pattern | `8443 -> 127.0.0.1:443` |

## Dashboard Validation

Successful authentication opened the Wazuh Overview page. The interface displayed areas including:

- Agents Summary
- Last 24 Hours Alerts
- Endpoint Security
- Threat Intelligence

At the time of validation, no endpoint agents were registered. Agent deployment was not required for this practice.

## Key Finding

The Wazuh all-in-one deployment completed successfully and all four core services were active. The dashboard was reachable from the Windows host through an SSH tunnel, demonstrating a controlled method for accessing the HTTPS interface while the server remained behind the VirtualBox NAT configuration.

## Skills Demonstrated

- Wazuh all-in-one deployment and component validation
- Wazuh manager, indexer, dashboard, and Filebeat service verification
- Linux service-status validation with `systemctl`
- SSH local port forwarding for secure administrative access
- HTTPS dashboard access and authentication validation
- SIEM platform deployment verification
- Credential-handling awareness and evidence redaction

## Tools and Commands

- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS
- Wazuh installation assistant
- Wazuh manager
- Wazuh indexer
- Wazuh dashboard
- Filebeat
- Windows PowerShell / OpenSSH client
- `systemctl is-active`
- SSH local port forwarding (`ssh -L`)
- Web browser over HTTPS

## Full Report

[View PDF report](report.pdf)

> The administrator password generated during installation is intentionally not included in this repository or README.
