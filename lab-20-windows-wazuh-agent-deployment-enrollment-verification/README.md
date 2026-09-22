# Lab 20 - Windows Wazuh Agent Deployment and Enrollment Verification

## Objective

Deploy a Wazuh agent on a Windows laboratory endpoint, connect it to the existing Wazuh server through the isolated `WAZUH-LAB` network, verify access to the required agent communication ports, validate the local Wazuh service, and confirm that the endpoint is successfully registered with an **Active** status in Wazuh.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Oracle VirtualBox
- Existing Wazuh all-in-one server
- Windows 10 Enterprise Evaluation endpoint
- VirtualBox Internal Network: `WAZUH-LAB`
- Wazuh server address: `10.10.20.10/24`
- Windows endpoint address: `10.10.20.30/24`
- Windows interface used for the laboratory path: `Ethernet 3`
- Wazuh agent version: `4.14.7`
- Windows PowerShell for network and service validation
- Existing SSH tunnel used for Wazuh dashboard access

## Key Activities

- Connected the Windows laboratory VM to the existing `WAZUH-LAB` VirtualBox Internal Network.
- Verified Wazuh server readiness and restarted the indexer, manager, Filebeat, and dashboard services.
- Assigned the static address `10.10.20.30/24` to the Windows laboratory interface.
- Tested connectivity from Windows to Wazuh TCP ports `1514` and `1515` with `Test-NetConnection`.
- Reused the existing SSH local-port-forwarding tunnel for Wazuh dashboard access.
- Used the Wazuh **Deploy new agent** workflow for a Windows endpoint.
- Installed the Wazuh Windows agent with the manager and registration server set to `10.10.20.10`.
- Started the Wazuh service and verified `wazuhsvc` as **Running** with PowerShell.
- Confirmed final Windows endpoint registration with an **Active** status in Wazuh.
- Reviewed the consolidated endpoint inventory containing both the Windows and previously registered Ubuntu agents.

## Laboratory Network

| Element | Address / Configuration | Purpose |
|---|---|---|
| Wazuh server | `10.10.20.10/24` | Manager and enrollment services |
| Windows endpoint | `10.10.20.30/24` | Windows system monitored by Wazuh |
| Internal network | `WAZUH-LAB` | Private VirtualBox communication path |
| Windows interface | `Ethernet 3` | Dedicated WAZUH-LAB interface |

The private internal network provided a direct communication path between the Windows endpoint and the Wazuh server while preserving the other adapters already present in the virtual machines.

## Connectivity Verification

Before installing the agent, PowerShell was used to verify connectivity to the Wazuh server.

| Validation | Observed Result | Meaning |
|---|---|---|
| TCP `1514` | `TcpTestSucceeded: True` | Agent communication service reachable |
| TCP `1515` | `TcpTestSucceeded: True` | Enrollment service reachable |

These checks confirmed that the Windows endpoint could reach the required Wazuh communication and enrollment services at `10.10.20.10`.

## Windows Agent Deployment

The Wazuh dashboard **Deploy new agent** workflow was used with the following settings:

| Setting | Value |
|---|---|
| Platform | Windows |
| Manager address | `10.10.20.10` |
| Agent name | `Windows-Agent` |
| Group | `default` |

The Wazuh `4.14.7` Windows MSI package was installed with `WAZUH_MANAGER` and `WAZUH_REGISTRATION_SERVER` set to `10.10.20.10` and `WAZUH_AGENT_NAME` set to `Windows-Agent`.

## Local Service Verification

After installation, the Wazuh service was started on Windows. PowerShell `Get-Service` confirmed:

| Service | Status |
|---|---|
| `wazuhsvc` | **Running** |

This verified that the agent service was operational locally before final dashboard validation.

## Enrollment Verification

The final Wazuh endpoint view confirmed successful registration:

| Field | Observed Value |
|---|---|
| Agent ID | `002` |
| Agent name | `Windows-Agent` |
| IP address | `10.10.20.30` |
| Operating system | Microsoft Windows 10 Enterprise Evaluation |
| Group | `default` |
| Cluster node | `node01` |
| Agent version | `v4.14.7` |
| Local service | `wazuhsvc` - Running |
| Final status | **Active** |

The **Active** status confirmed successful manager-agent communication from the Windows endpoint.

## Consolidated Endpoint Inventory

At the time of the final capture, Wazuh displayed two registered agents in the `default` group:

| Agent | Address | Status |
|---|---|---|
| `Windows-Agent` | `10.10.20.30` | **Active** |
| `ubuntu-agent` | `10.10.20.20` | Disconnected |

The Ubuntu endpoint remained registered from the previous laboratory, while the new Windows endpoint was actively reporting during the Day 20 validation.

## Key Finding

The laboratory successfully extended the Wazuh environment to a Windows endpoint. The Windows VM communicated with the server through the isolated `WAZUH-LAB` network, both required TCP ports were reachable, the local Wazuh service was running, and `Windows-Agent` appeared in Wazuh with an **Active** status.

## Skills Demonstrated

- Wazuh Windows agent deployment and enrollment
- Windows endpoint network configuration for SIEM communication
- Wazuh agent-port validation with PowerShell `Test-NetConnection`
- Windows service verification with `Get-Service`
- Endpoint registration and active-status validation in Wazuh
- Multi-endpoint Wazuh inventory review
- Technical documentation and evidence collection

## Tools and Commands

- Oracle VirtualBox
- Windows 10 Enterprise Evaluation
- Wazuh manager
- Wazuh dashboard / Endpoints
- Wazuh Windows agent
- Windows PowerShell
- `Get-NetAdapter`
- `New-NetIPAddress`
- `ipconfig`
- `Test-NetConnection`
- `Get-Service`
- Windows Installer / MSI
- OpenSSH / SSH local port forwarding

## Full Report

[View PDF report](report.pdf)

> All network communication, endpoint enrollment, and verification documented in this laboratory were performed in an isolated and authorized training environment.
