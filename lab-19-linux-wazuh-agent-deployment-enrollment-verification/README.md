# Lab 19 - Linux Wazuh Agent Deployment and Enrollment Verification

## Objective

Deploy a Wazuh agent on a separate Ubuntu Linux endpoint, establish isolated communication with the existing Wazuh server, verify the required enrollment and communication services, and confirm that the endpoint is successfully registered with an **Active** status in Wazuh.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Oracle VirtualBox
- Existing Wazuh all-in-one server
- Separate Ubuntu Linux endpoint
- VirtualBox Internal Network: `WAZUH-LAB`
- Wazuh server address: `10.10.20.10/24`
- Ubuntu agent address: `10.10.20.20/24`
- Dedicated interface on both systems: `enp0s9`
- Wazuh agent package: `4.14.7-1` for amd64
- Windows host used for Wazuh dashboard access through the existing SSH tunnel

## Key Activities

- Added a dedicated VirtualBox Internal Network adapter to the Wazuh server and Ubuntu endpoint.
- Configured the private `WAZUH-LAB` network for server-to-endpoint communication.
- Assigned `10.10.20.10/24` to the Wazuh server and `10.10.20.20/24` to the Ubuntu endpoint.
- Verified bidirectional ICMP connectivity with 0% packet loss.
- Restarted and validated the `wazuh-manager` service before enrollment.
- Confirmed that TCP `1515` was listening for agent enrollment through `wazuh-authd`.
- Confirmed that TCP `1514` was listening for agent communication through `wazuh-remoted`.
- Reused the existing SSH local-port-forwarding tunnel to access the Wazuh dashboard.
- Used the **Deploy new agent** workflow from the Wazuh Endpoints interface.
- Installed the Linux Wazuh agent package on the Ubuntu endpoint.
- Enabled and started the `wazuh-agent` service with `systemctl`.
- Verified final registration and an **Active** endpoint state in the Wazuh dashboard.

## Laboratory Network

| Element | Address / Configuration | Purpose |
|---|---|---|
| Wazuh server | `10.10.20.10/24` | Central manager and enrollment services |
| Ubuntu agent | `10.10.20.20/24` | Linux endpoint monitored by Wazuh |
| Internal network | `WAZUH-LAB` | Private VirtualBox communication path |
| Interface | `enp0s9` | Dedicated laboratory interface on both systems |

The dedicated internal network provided direct communication between the Wazuh server and endpoint while preserving the other adapters already used by the virtual machines.

## Connectivity and Server Readiness

Before deploying the agent, communication was validated in both directions.

| Validation | Observed Result |
|---|---|
| Agent -> server | 4/4 ICMP replies, 0% packet loss |
| Server -> agent | 4/4 ICMP replies, 0% packet loss |
| Wazuh manager | Active |
| TCP 1515 | Listening through `wazuh-authd` for enrollment |
| TCP 1514 | Listening through `wazuh-remoted` for agent communication |

This confirmed that the server was reachable and that the required Wazuh agent ports were available before enrollment.

## Linux Agent Deployment

The Wazuh dashboard **Deploy new agent** workflow was used with the following settings:

| Setting | Value |
|---|---|
| Package | Linux DEB amd64 |
| Manager address | `10.10.20.10` |
| Agent name | `ubuntu-agent` |
| Group | `default` |

The generated installation command downloaded and installed Wazuh agent version `4.14.7-1` on the Ubuntu endpoint. After installation, systemd was reloaded and the agent service was enabled and started.

## Enrollment Verification

The final Wazuh Endpoints view confirmed successful enrollment:

| Field | Observed Value |
|---|---|
| Agent ID | `001` |
| Agent name | `ubuntu-agent` |
| IP address | `10.10.20.20` |
| Operating system | Ubuntu 20.04 LTS |
| Group | `default` |
| Cluster node | `node01` |
| Agent version | `v4.14.7` |
| Final status | **Active** |

The Active status confirmed successful manager-agent communication after deployment.

## Key Finding

The laboratory successfully extended the existing Wazuh environment from a standalone all-in-one server to a monitored Linux endpoint. The server and agent communicated through the isolated `WAZUH-LAB` network, the required enrollment and event-communication listeners were verified, and the Linux endpoint appeared in Wazuh as an **Active** registered agent.

## Skills Demonstrated

- Wazuh Linux agent deployment and enrollment
- Wazuh manager-agent connectivity validation
- Wazuh enrollment and communication port verification
- VirtualBox internal-network configuration for SIEM endpoints
- Linux service initialization and validation with `systemctl`
- Endpoint registration and active-status verification in Wazuh
- Technical documentation and evidence collection

## Tools and Commands

- Oracle VirtualBox
- Ubuntu Linux
- Wazuh manager
- Wazuh dashboard / Endpoints
- Wazuh agent
- `wazuh-authd`
- `wazuh-remoted`
- OpenSSH / SSH local port forwarding
- `ip`
- `ping`
- `ss`
- `systemctl`
- `wget`
- `dpkg`

## Full Report

[View PDF report](report.pdf)

> All network communication and endpoint enrollment documented in this laboratory were performed in an isolated and authorized training environment.
