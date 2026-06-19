

# process-monitoring


## Objective

Investigate process execution activity generated during attack simulation using Sysmon and Windows Security logs.


## Activity Generated

```powershell
powershell
cmd
whoami
hostname
ipconfig
tasklist
systeminfo
```

## Search Queries

Sysmon

###  Sysmon  Query

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" |
Where-Object {$_.Id -eq 1}
```


## Splunk  Search Query

```spl
EventCode=1
```


```EventCode=1

```

Windows Security

###  Sysmon  Query


```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4688}
```
## Splunk  Search Query

```
EventCode=4688
```

Event Description

Event ID   Source	       Description
1	   Sysmon	       Process Creation
4688 	   Windows Security    New Process Created

 

## Findings

Observed process execution activity including:

- powershell.exe
- cmd.exe
- whoami.exe
- hostname.exe
- ipconfig.exe
- tasklist.exe
 Check:
 - process names
 - PowerShell activity
 - suspicious command execution

## Evidence
process-created.png
process_sysmon-log-1.png
process-sysmon-logs-4688.png
splunk_event_1.png
splunk_process_creation_4688.png



## SOC Relevance
Process creation telemetry is one of the most valuable data sources for detecting attacker execution.
Process creation telemetry is useful for detecting:
- malicious process execution
- attacker tools
- PowerShell abuse
- command-line activity



