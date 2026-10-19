
# 02 - Log Management (Sysmon Setup)

## Objective
Set up endpoint logging using Sysmon so that all system activities can be monitored and analyzed in a SOC environment.


## Purpose:
Sysmon captures detailed endpoint telemetry useful for SOC investigations and threat hunting

It helps SOC analysts detect:

Process execution
Network connections
File creation
Malware behavior 
attacker tools
abnormal behavior.
PowerShell activity
Suspicious command execution


## Step 1 — Install Sysmon

Download: Sysmon  ( windows VM --> Open Administrator CMD)

Run command:

```
sysmon64.exe -i

```

Run:

 ``` sc query sysmon64```

output:  STATE: RUNNING

## Verify

Open:Event Viewer

Go: Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

If logs appear, installation succeeded.


## Step 2 — Install Better Config

Download:SwiftOnSecurity Sysmon Config   ( windows VM --> Open Administrator CMD) 

Run:

```
sysmon64.exe -i sysmonconfig-export.xml

```

## Step 3: Verify Logs in Event Viewer

Path:
Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

If logs appear, Sysmon is working correctly.


## Step 4: Sysmon Event IDs Used

Event ID     Meaning
1            Process Creation
3            Network Connection
5            Process Termination
16           Sysmon Configuration Change
22           DNS Query

## Evidence - screenshots
- sc-query.png
- event-viwer.png

## SOC Relevance

Sysmon helps detect:
- Malware execution
- Suspicious processes
- Network communication
- DNS-based attacks
- Threat hunting activities


---
