# Lab 1 - Isolated Virtual Network Laboratory

## Objective

Build and verify an isolated virtual network where Ubuntu and Windows systems can communicate with each other without external network access.

## Environment

- Oracle VirtualBox
- Ubuntu 24.04 LTS
- Windows 10
- Internal VirtualBox network: `LAB-NET`

## Activities

- Prepared Ubuntu and Windows virtual machines.
- Connected both systems to the same internal VirtualBox network.
- Configured static IPv4 addresses in the `10.10.10.0/24` subnet.
- Verified the configured addresses with `ip a` and `ipconfig`.
- Tested bidirectional connectivity using ICMP ping.
- Verified that the laboratory network had no Internet connectivity.

## Key Results

- Ubuntu: `10.10.10.10/24`
- Windows: `10.10.10.20/24`
- Bidirectional communication was successful with 0% packet loss.
- External connectivity failed as expected, confirming network isolation.

## Skills Demonstrated

- Virtual network configuration
- IPv4 addressing
- Linux and Windows network verification
- ICMP connectivity testing
- Safe laboratory isolation

## Full Report

[View the complete PDF report](./report.pdf)
