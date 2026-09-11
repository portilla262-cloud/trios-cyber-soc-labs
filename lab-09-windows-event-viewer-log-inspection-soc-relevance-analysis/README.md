# Lab 9 - Windows Event Viewer Log Inspection and SOC Relevance Analysis

## Objective

Inspect native Windows event logs using Event Viewer and evaluate the SOC relevance of representative Security, System, and Application events by analyzing authentication activity, privileged logons, service installation, system warnings, and application errors.

## Environment

- Windows virtual machine
- Oracle VirtualBox
- Windows Event Viewer
- Native Windows Security, System, and Application logs
- Authorized isolated laboratory environment

## Tools and Logs

- Windows Event Viewer (`eventvwr.msc`)
- Security log
- System log
- Application log
- Microsoft Windows security auditing
- Service Control Manager
- DistributedCOM
- Defrag
- Application Error

## Key Activities

- Prepared a Windows virtual machine for native event-log inspection.
- Opened Windows Event Viewer and reviewed the Security, System, and Application log categories.
- Analyzed Event ID `4624` to identify a successful account logon.
- Reviewed Event ID `4672` to identify a logon session that received special privileges.
- Investigated Event ID `4625` to examine failed-logon details, including the affected account, failure reason, logon type, process, source address, and authentication package.
- Reviewed Event ID `7045` to identify service installation activity and assess its potential relevance to software deployment or persistence.
- Examined Event ID `10016` from DistributedCOM as supporting system and timeline context.
- Reviewed Event ID `264` from Defrag as operational and system-health context.
- Analyzed Event ID `1000` to examine an `explorer.exe` application crash and its potential value during endpoint investigations.
- Applied focused Event Viewer filtering across multiple event IDs and log categories.
- Compared the investigative value of selected Windows events and assessed their relevance to SOC analysis.

## Key Findings

The laboratory demonstrated that Windows event logs provide different levels of investigative value depending on the event type and surrounding context.

- Event `4624`: successful account logon - SOC relevant
- Event `4672`: special privileges assigned to a new logon - SOC relevant
- Event `4625`: failed account logon - high SOC relevance
- Event `7045`: service installed in the system - high SOC relevance
- Event `10016`: DistributedCOM permission warning - conditionally relevant
- Event `264`: storage optimization error - conditionally relevant
- Event `1000`: `explorer.exe` application crash - relevant or conditional depending on context

The failed-logon event (`4625`) provided detailed authentication context such as account name, failure reason, process, source address, logon type, and authentication package. The service-installation event (`7045`) also had strong investigative value because unexpected services may require validation for persistence or malicious service creation.

The activity reinforced that a Windows event should not automatically be treated as a security incident. SOC analysis requires correlation with the event source, user, frequency, surrounding activity, and investigation objective.

## Skills Demonstrated

- Windows Event Viewer log analysis
- Windows Security, System, and Application log inspection
- Windows authentication event analysis
- Successful and failed logon investigation
- Privileged logon analysis
- Windows event ID filtering
- Service-installation event analysis
- Event correlation and timeline context
- SOC relevance assessment
- Distinguishing security-relevant events from operational noise
- Endpoint investigation and contextual interpretation
- Technical evidence collection and documentation

## Full Report

[View PDF report](report.pdf)

> All activities were performed in an isolated and authorized laboratory environment.
