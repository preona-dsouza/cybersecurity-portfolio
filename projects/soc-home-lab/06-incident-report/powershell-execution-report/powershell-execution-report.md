


### Incident Report – Powershell activity  Detection

## Incident Summary
A security alert was triggered following the execution of PowerShell on a Windows endpoint. 
PowerShell is a legitimate administrative tool but is frequently abused by attackers for scripting, fileless malware execution, and post-exploitation activities.


severity : Medium
Date: 31/05/2026 19:30

## Detection Source

Splunk Detection Rule – Powershell Detection
```
index=* EventCode=4688
| search process_name="powershell.exe"
```

##  Observed Data
Event Code: 4688 (Process Creation)
Computer Name: DESKTOP-LBVGK57  
User: DESKTOP-LBVGK57\Pre
Process Name: powershell.exe
Process Path: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
Parent Process: C:\Windows\explorer.exe
Token Elevation Type: Limited (Type 3)
Integrity Level: Medium Mandatory Level
Command Line: Not Available


## Investigation
- Reviewed Windows Security logs for EventCode 4688
- Identified creation of powershell.exe by user Pre
- Confirmed parent process was explorer.exe, indicating interactive user execution
- Verified PowerShell was launched with a limited user token i.e standard user priviliges (non-elevated)
- No suspicious parent-child process relationship observed
- No command-line arguments were captured for further analysis
- No immediate indicators of malicious execution were identified

##  Impact
- PowerShell execution was detected on the endpoint
- PowerShell is a legitimate administrative tool but can be abused by attackers
- No evidence of privilege escalation or malicious activity was observed
- Impact is currently assessed as low


##  Conclusion
The alert identified the execution of powershell.exe by the user Pre. The process was launched interactively from explorer.exe using a standard user token. 
Based on the available evidence, the activity appears consistent with legitimate user behavior and no signs of malicious activity were observed.


##  Recommendation
- Monitor PowerShell executions for unusual frequency or behavior
- Enable PowerShell Script Block Logging and Module Logging
- Capture command-line arguments for future investigations
- Correlate PowerShell activity with network and authentication events
- Investigate executions originating from unusual parent processes
- Review repeated PowerShell activity across multiple endpoints
