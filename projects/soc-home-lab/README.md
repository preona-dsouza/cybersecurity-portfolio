
# SOC Home Lab – Splunk SIEM & Threat Detection

## Overview

This project demonstrates the  implementation of a Security Operations Center (SOC) Home Lab for  security monitoring, threat detection, investigation, and incident reporting.

The goal was to gain practical experience with log collection, threat detection, threat hunting, and incident investigation using industry-standard tools. Throughout the project, 
I generated security events, analyzed logs, created detection rules, and documented investigations to better understand day-to-day SOC operations.

---

## Objectives

* Build a SOC environment
* Collect endpoint telemetry using Sysmon
* Centralize logs using Splunk Enterprise
* Simulate attacker activity
* Perform threat hunting and log analysis
* Create SIEM detection rules
* Produce incident investigation reports

---

## Lab Environment

| Component              | Purpose            |
| ---------------------- | ------------------ |
| Kali Linux             | Attacker Machine   |
| Windows 10             | Target/Endpoint    |
| Sysmon                 | Endpoint Telemetry |
| Splunk Enterprise      | SIEM Platform      |
| Oracle VirtualBox      | Virtualization     |
| NAT & Internal Network | Lab Networking     |

---

## Project Workflow

### 1. SOC Architecture
Created a virtual lab environment consisting of a Windows endpoint, a Kali Linux attacker machine, and Splunk Enterprise for centralized log collection and analysis.
* Virtualized SOC environment
* Network connectivity 
* Architecture documentation

### 2. Log Management

* Sysmon instalation and deployment
* Windows Event Logs collection 
* Splunk installation and configuration
* Log ingestion validation 
sysmon installed into windows system to collect endpoint telementry and configured  splunk to ingest abd analyze logs

### 3. Attack Simulation

Security events generated for detection testing:
* Failed Login Attempts
* DNS Activity
* Network Connections
* PowerShell Execution
* Suspicious Process Execution
* Nmap Reconnaissance

### 4. Threat Hunting

Investigated:
* Failed Authentication Events (4625)
* Successful Login Events(4624)
* DNS Queries (Sysmon Event ID 22)
* Network Connections (Sysmon Event ID 3)
* Process Creation Events (Sysmon Event ID 1)
* PowerShell Activity


### 5. Detection Engineering

Developed Splunk alerts for:

#### Brute Force Detection

Event ID:

* 4625 (Failed Logon)


#### Network Activity Detection

Event ID:

* 3 (Network Connection)

Detection Logic:



#### PowerShell Execution Monitoring

Monitors PowerShell-related process execution activity for investigation.

---

## Incident Reporting

Created investigation reports for:

* Brute Force Authentication Attempts
* Network Connection Alerts
* PowerShell Execution Activity

Each report includes:

* Incident Summary
* Detection Source
* Evidence
* Investigation Findings
* Recommendations

---

## Skills Demonstrated

* Security Operations Center (SOC)
* SIEM Administration
* Splunk SPL
* Sysmon Configuration
* Windows Event Log Analysis
* Threat Hunting
* Detection Engineering
* Incident Investigation
* Log Management
* Security Monitoring
* Network Security
* Incident Response

---

## Repository Structure

```
SOC-Home-Lab
│
├── 01-Architecture
├── 02-Log-Management
├── 03-Attack-Simulation
├── 04-Threat-Hunting
├── 05-Detection-Engineering
├── 06-Incident-Reports

```

---

## Key Outcome

Successfully built an end-to-end SOC Home Lab capable of generating, collecting, detecting, investigating, and documenting security events using industry-standard tools and methodologies.
