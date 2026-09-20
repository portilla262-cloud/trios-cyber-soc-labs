# Lab 18 - Wazuh Component Health Check and Post-Installation Verification

## Objective

Verify the operational health of the Wazuh all-in-one deployment after installation, confirm remote and browser accessibility, revalidate the core services and storage state, and document the troubleshooting actions required to stabilize the Wazuh server.

## Environment

- Authorized TRIOS CYBER laboratory environment
- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS (x86_64)
- Dedicated Wazuh all-in-one server VM
- Wazuh manager
- Wazuh indexer
- Wazuh dashboard
- Filebeat
- VirtualBox NAT networking
- Windows host for SSH administration and dashboard access
- Server hostname: `trioscyber`
- Server address: `10.0.2.15`

## Key Activities

- Connected remotely to the Wazuh server through SSH using VirtualBox NAT port forwarding.
- Verified the Wazuh manager, indexer, dashboard, and Filebeat with `systemctl is-active`.
- Re-established the SSH local-port-forwarding tunnel for dashboard access.
- Confirmed that the Wazuh HTTPS login interface was reachable from the Windows host.
- Authenticated to the Wazuh dashboard and validated the Overview page.
- Confirmed that no endpoint agents were registered at this stage, as agent deployment was outside the scope of the practice.
- Reviewed root-filesystem capacity after storage expansion.
- Revalidated all four Wazuh services after browser and storage checks.
- Documented the installation and post-installation troubleshooting performed to obtain a stable deployment.

## Core Component Health Check

| Component | Verification | Result |
|---|---|---|
| Wazuh manager | `systemctl is-active wazuh-manager` | Active |
| Wazuh indexer | `systemctl is-active wazuh-indexer` | Active |
| Wazuh dashboard | `systemctl is-active wazuh-dashboard` | Active |
| Filebeat | `systemctl is-active filebeat` | Active |

## Remote and Dashboard Access

| Access Element | Observed Value |
|---|---|
| SSH connection | `matthew@127.0.0.1` using host port `2222` |
| Windows browser endpoint | `https://127.0.0.1:8443` |
| Forwarded destination | `127.0.0.1:443` on the Wazuh server |
| Dashboard state | Login page and authenticated Overview accessible |

The SSH tunnel allowed the dashboard to remain behind the VirtualBox NAT configuration while still being reachable from the Windows host.

## Storage Verification

After the troubleshooting and storage expansion, the root filesystem reported approximately:

| Metric | Observed Value |
|---|---|
| Root filesystem size | 97 GB |
| Used | 19 GB |
| Available | 74 GB |
| Utilization | 21% |

This confirmed that the Wazuh server had sufficient free storage for continued laboratory use.

## Troubleshooting Performed

The laboratory documented several issues encountered during deployment and the corrective actions used to recover the server:

| Issue | Corrective Action | Final Result |
|---|---|---|
| Root filesystem too small / `No space left on device` | Expanded the LVM physical volume and root logical volume | Root filesystem increased to approximately 97 GB |
| Incomplete Wazuh package state | Removed residual `wazuh-manager` state and `/var/ossec`, repaired `dpkg`, and restarted installation | Clean all-in-one installation completed |
| Wazuh API initialization timing | Allowed additional API initialization time before requesting the API token | Installation progressed successfully |
| VirtualBox `BLKCACHE_IOERR` interruption | Checked host storage, resumed the VM, and continued the installation | Deployment completed without rebuilding the VM |
| ext4 filesystem inconsistency after I/O interruption | Repaired the root logical volume with `fsck.ext4` and repeated the check until clean | Ubuntu booted normally and Wazuh services returned active |

## Health Check Summary

The final verification confirmed that:

- Remote SSH access to `trioscyber` was successful.
- Wazuh manager was operational.
- Wazuh indexer was operational.
- Wazuh dashboard was operational.
- Filebeat was operational.
- The HTTPS login interface was accessible through the SSH tunnel.
- Authentication successfully opened the Wazuh Overview page.
- The root filesystem had adequate available capacity after expansion.

## Key Finding

The Wazuh all-in-one server remained operational after installation troubleshooting and filesystem recovery. Service-level checks, browser-level validation, and storage verification all confirmed a stable post-installation state suitable for the next laboratory activities.

## Skills Demonstrated

- Wazuh post-installation health checking and operational verification
- Wazuh manager, indexer, dashboard, and Filebeat service validation
- SSH-based remote administration and local port forwarding
- Linux storage and LVM troubleshooting
- Filesystem recovery with `fsck.ext4`
- Package-state cleanup and deployment recovery
- SIEM infrastructure troubleshooting and post-installation validation
- Technical troubleshooting documentation and evidence collection

## Tools and Commands

- Oracle VirtualBox
- Ubuntu Server 24.04.4 LTS
- Wazuh manager
- Wazuh indexer
- Wazuh dashboard
- Filebeat
- Windows PowerShell / OpenSSH client
- `systemctl is-active`
- `df -h`
- LVM tools
- `dpkg`
- `fsck.ext4`
- SSH local port forwarding (`ssh -L`)
- Web browser over HTTPS

## Full Report

[View PDF report](report.pdf)

> Credentials and sensitive authentication information are intentionally not reproduced in this repository.
