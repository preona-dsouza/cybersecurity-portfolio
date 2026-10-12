
# SOC Home Lab – Splunk SIEM & Threat Detection

## Overview

This project documents a Security Operations Center (SOC) Home Lab built to practice security monitoring, threat detection, threat hunting and incident investigation and reporting using Splunk Enterprise, Sysmon, and Windows event logs.

The project covers endpoint telemetry collection, log analysis, security-event investigation, detection-rule development, and incident reporting. 
Security-related activities were simulated in VM lab environment, and resulting evidence was documented to develop practical SOC investigation skills.

---

## Objectives

* Build and document a virtual SOC lab environment.
* Collect Windows endpoint telemetry using Sysmon.
* Ingest and investigate security events using Splunk Enterprise.
* Simulate controlled security-related activity.
* Perform threat hunting and log analysis.
* Develop SPL searches for security monitoring and detection.  
* Document investigation findings and recommendations in incident reports.

---

## Lab Environment

| Component              | Purpose                                            |
| ---------------------- | -------------------------------------------------- |
| Kali Linux             | Lab machine for controlled security testing        |
| Windows 10             | Target endpoint generating Windows security events |
| Sysmon                 | Endpoint telemetry collection                      |
| Splunk Enterprise      | SIEM platform for log searching and investigation  |
| Oracle VirtualBox      | Virtualization                                     |
| Virtual networking     | Lab component connectivity                         |

---

## Project Workflow

### 1. SOC Architecture
Documented the virtual lab environment, including the Windows endpoint, Kali Linux machine, virtualization platform, and networking setup.
* Architecture documentation
* Virtual machine connectivity
* Network configuration 
  

### 2. Log Management
Configured endpoint telemetry collection and investigated Windows and Sysmon events using Splunk.
* Sysmon installation and deployment
* Windows Event Log collection 
* Splunk Enterprise setup and log ingestion 
* Initial event-ingestion validation 


### 3. Attack Simulation

Security events generated for investigation and detection testing:
* Failed Login Attempts
* DNS Activity
* Network Connections
* PowerShell Execution
* Suspicious Process Execution
* Nmap Reconnaissance

These activities provide investigation scenarios; the presence of an event alone does not establish malicious intent.

### 4. Threat Hunting

Investigated Windows and Sysmon telemetry using event identifiers and Splunk searches.
* Failed Authentication Events (Event ID 4625)
* Successful Logon Events(Event ID 4624)
* DNS Queries (Sysmon Event ID 22)
* Network Connections (Sysmon Event ID 3)
* Process Creation Events (Sysmon Event ID 1)
* PowerShell Activity


### 5. Detection Engineering

Developed and documented Splunk searches for selected endpoint security use cases.  

#### Repeated Authentication Failures

* Windows Security Event ID 4625
* Investigation of repeated failed logon events


#### Network Activity Detection

* Sysmon Event ID 3
* Investigation of source and destination details, ports, and connection patterns where available


#### PowerShell Execution Monitoring

* Windows Security Event ID 4688
* Investigation of PowerShell process execution and associated event details

---

## Incident Reporting

Documented investigation reports for the following use cases:

* Brute Force Authentication Attempts
* Network Connection Alerts
* PowerShell Execution Activity

Each report documents relevant incident details, detection logic, available evidence, investigation findings, and recommendations. Findings distinguish observed activity from suspected threats and potential false positives.

---

## Skills Demonstrated

* Splunk SIEM and SPL searches 
* Windows Security Event Log analysis
* Sysmon telemetry investigation
* Authentication-event analysis
* Process-execution investigation
* Network-event analysis
* Threat hunting fundamentals
* Detection-rule development
* Incident investigation and reporting
* Security monitoring and log management

---

## MITRE ATT&CK Mapping

|# |	Rule / Activity	                       | Technique              	                      | Tactic              |
---------------------------------------------------------------------------------------------------------------------
|1 |  Repeated Failed Login Attempts	       | T1110 – Brute Force	                          | Credential Access   |
|2 |  Nmap Reconnaissance	                   | T1046 – Network Service Discovery              | Discovery	          |
|3 |	PowerShell Execution	                 | T1059.001 – PowerShell	                        | Execution           |
|4 |	Suspicious Process / System Discovery	 | T1082 – System Information Discovery	          | Discovery           |

Note: These are potential technique mappings based on the documented lab activities, not confirmation of malicious activity.
---


## Repository Structure

```
soc-home-lab/
├── 01-architecture/
├── 02-log-analysis/
├── 03-attack-simulation/
├── 04-threat-hunting/
├── 05-Detection-engineering/
├── 06-incident-report/
├── screenshots/
└── README.md

```

---

## Key Outcome

Successfully built an end-to-end SOC Home Lab covering endpoint telemetry, SIEM-based investigation, detection logic, threat hunting, and incident reporting.


## Scope and Limitations

This is a personal cybersecurity learning project. The documented findings reflect the events and evidence available in the lab. Detection rules require appropriate log sources, field validation, and testing before they can be considered production-ready.
