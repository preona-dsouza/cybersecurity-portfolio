

# Splunk Installation and Log Ingestion

## Splunk Enterprise SOC Lab Setup

## Objective

Deploy Splunk Enterprise as the central SIEM platform for log collection, investigation, and detection engineering.

| Section            | Purpose           |
|--------------------|-------------------|
| Search & Reporting | Investigate logs  |
| Dashboards         | Visual monitoring |
| Alerts             | Detection rules   |
| Data Inputs        | Log collection    |


## Environment

| Component         | Purpose            |
|-------------------|--------------------|
| Windows 11        | Log Source         |
| Sysmon            | Endpoint Telemetry |
| Splunk Enterprise | SIEM               |



## Install Splunk


Install:Splunk Enterprise

Open:http://127.0.1.0:8000

Create:
Admin Username
Admin Password

Open Administrator CMD:

net stop splunkd
net start splunkd


Configure Splunk Universal Forwarder

splunk add forward-server

splunk restart

splunk list forward-server


Screenshot:
splunk-installation.png
splunk-login.png
splunk-verification.png

## Configuration

Installed Splunk Enterprise and configured local log collection.

Enabled:

- Security Logs
- System Logs
- Application Logs
- Sysmon Operational Logs

# Log Ingestion


In Splunk: Settings → Add Data -> Monitor ->  Local Event Logs

Choose:

Local Event Logs

Select:
- Security
- System
- Application
- Microsoft-Windows-Sysmon/Operational

## Validation

Splunk -> Go to:Apps → Search & Reporting
Search:

```spl
index= *

```
purpose: Search All Logs


Findings
Logs were successfully ingested into Splunk.
- Windows logs
- Sysmon events
- authentication activity


## SOC Relevance

SIEM platforms provide centralized visibility into endpoint and network activity.
