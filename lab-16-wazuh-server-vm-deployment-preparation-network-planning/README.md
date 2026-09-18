# Lab 16 - Wazuh Server VM Deployment Preparation and Network Planning

## Objective

Prepare and validate a dedicated Ubuntu Server virtual machine before deploying a Wazuh server. The activity focuses on operating-system compatibility, network connectivity, hardware resources, storage availability, administrative privileges, and documenting the final network plan required for the next installation stage.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS (x86_64)
- Dedicated virtual machine with hostname `trioscyber`
- VirtualBox NAT networking
- Administrative user `matthew` with `sudo` privileges
- Wazuh not yet installed; this practice covers pre-installation readiness only

## Virtual Machine Configuration

| Resource | Configuration / Observed Value |
|---|---|
| Operating system | Ubuntu Server 24.04.4 LTS (x86_64) |
| Hostname | `trioscyber` |
| Memory | 4096 MB configured / ~3.8 GiB detected |
| CPU | 2 vCPU |
| Virtual disk | 100 GB |
| Root logical volume | ~9.8 GB |
| Free space on root LV | ~6.5 GB during the check |
| Network adapter | Intel PRO/1000 MT Desktop |
| Network mode | NAT |

## Network Plan

| Parameter | Final Plan |
|---|---|
| Virtual machine role | Wazuh Server |
| VirtualBox network mode | Adapter 1 - NAT |
| Server interface | `enp0s3` |
| IPv4 address | `10.0.2.15/24` (DHCP) |
| Default gateway | `10.0.2.2` |
| Connectivity test | `8.8.8.8` reachable with 0% packet loss |
| Hostname | `trioscyber` |
| Administrative account | `matthew` with `sudo` privileges |
| Installation state | Wazuh not yet installed - preparation completed first |

## Key Activities

- Created and started a dedicated Ubuntu Server VM in Oracle VirtualBox for the planned Wazuh deployment.
- Verified the operating system, hostname, and `x86_64` architecture before installation.
- Reviewed IP addressing and routing with `ip -br a` and `ip route`.
- Confirmed external IP connectivity with ICMP testing to `8.8.8.8`.
- Checked memory and CPU availability with `free -h` and `nproc`.
- Reviewed disk layout and root-filesystem capacity with `lsblk` and `df -h /`.
- Verified administrative access using `whoami`, `sudo -v`, and `sudo -l`.
- Consolidated the results into a pre-installation readiness assessment.
- Documented the final network plan before proceeding to Wazuh installation.

## Pre-Installation Readiness Assessment

| Check | Observed Result | Status |
|---|---|---|
| Supported OS / architecture | Ubuntu 24.04.4 LTS, x86_64 | Ready |
| Hostname | `trioscyber` | Ready |
| IP connectivity | `10.0.2.15/24` via NAT; `8.8.8.8` reachable | Ready |
| RAM | ~3.8 GiB detected | Ready |
| CPU | 2 virtual cores | Ready - minimum |
| Disk | 100 GB virtual disk; ~6.5 GB free on current root LV | Review for growth |
| Administrative access | `matthew` with sudo ALL privileges | Ready |

## Key Finding

The VM met the main pre-installation checks for a small Wazuh laboratory deployment. The principal resource item identified for future review was storage allocation: although the VirtualBox disk is 100 GB, the current root logical volume exposes only about 9.8 GB, so the root/LVM allocation should be expanded if the deployment grows or begins retaining larger volumes of security data.

## Skills Demonstrated

- Wazuh server deployment preparation and pre-installation assessment
- Ubuntu Server system and architecture verification
- Virtual machine resource validation
- Linux IP configuration and routing verification
- Network connectivity testing
- Disk and LVM capacity review
- Linux administrative-access validation
- Infrastructure and network planning for SIEM deployment

## Tools and Commands

- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS
- `ip -br a`
- `ip route`
- `ping`
- `free -h`
- `nproc`
- `lsblk`
- `df -h /`
- `whoami`
- `sudo -v`
- `sudo -l`
- `hostname`
- `uname -m`

## Full Report

[View PDF report](report.pdf)

> This practice documents preparation and readiness checks only. Wazuh was not installed during this laboratory stage.
