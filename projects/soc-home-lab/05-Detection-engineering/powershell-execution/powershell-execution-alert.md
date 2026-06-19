

### PowerShell Execution Detection

## Objective

Detect execution of PowerShell processes that may indicate malicious scripting activity, reconnaissance, or post-exploitation behavior within Windows environments.


## Data Source

Windows Security Event Logs (Process Creation)

|Event Code  |	Description           |
|------------|------------------------|
|4688	     | Process Creation Event |


## Detection rule/Alert

```
index=windows EventCode=4688
| search process_name="powershell.exe"
```


## Alert Configuration
Type: Scheduled
Severity: Medium 
Condition: execution of powershell.exe
Time Range: Last 1 hour 


## Logic

This detection rule focuses on Windows process creation telemetry (EventCode 4688) to identify instances where PowerShell is executed on a system.
- Collects Windows process creation logs (EventCode=4688)
- Filters events where process_name="powershell.exe"
- Alert triggers when the number of results is greater than 2


## Analysis

PowerShell activity may indicate potential malicious execution (common attacker tool)

Suspicious scenarios include:
- PowerShell launched from unusual parent processes (e.g., winword.exe, excel.exe, cmd.exe)
- Execution by non-admin users
- Encoded or obfuscated commands 


## SOC Relevance

This detection is important in SOC environments because repeated PowerShell execution can indicate malicious activity such as fileless attacks or post-exploitation behavior.
It  helps analysts quickly identify abnormal scripting activity for further investigation. 
