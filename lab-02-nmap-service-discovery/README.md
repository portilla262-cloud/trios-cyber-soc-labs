# Lab 2 - Nmap Scanning and Service Discovery

## Objective

Perform authorized host discovery, port scanning and service identification against an intentionally vulnerable Metasploitable 2 system inside an isolated network.

## Environment

- Oracle VirtualBox
- Ubuntu scanning system
- Metasploitable 2 target
- Internal VirtualBox network: `LAB-NET`

## Activities

- Prepared and started a Metasploitable 2 virtual machine.
- Connected the scanner and target to the same isolated virtual network.
- Assigned the target the address `10.10.10.30/24`.
- Verified connectivity between the Ubuntu scanner and the target.
- Installed and used Nmap for host discovery.
- Identified live hosts in the isolated subnet.
- Performed service and version discovery against the Metasploitable target.
- Reviewed the exposed services from a security perspective.

## Key Findings

The target exposed multiple intentionally vulnerable or legacy services, including FTP, SSH, Telnet, HTTP, SMB, NFS, MySQL, PostgreSQL, VNC, IRC, AJP13 and Apache Tomcat.

The exercise demonstrated how service enumeration can help identify unnecessary or risky network exposure in a controlled environment.

## Skills Demonstrated

- Nmap host discovery
- Port scanning
- Service enumeration
- Network exposure review
- Working safely with an intentionally vulnerable target

## Full Report

[View the complete PDF report](./report.pdf)
