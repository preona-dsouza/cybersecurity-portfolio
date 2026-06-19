### Sysmon Analysis


Purpose:
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


 Sysmon  PowerShell

Used PowerShell to investigate Sysmon logs.

Sysmon Event Query

```
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" | Select -First 20	
```
purpose: Show Sysmon security logs

Event ID     Meaning
1	     Process Creation
3	     Network Connection
5	     Process Termination
16	     Sysmon Configuration Change
22	     DNS Query

## Filter Process Creation Events 

Run:
```
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" | Where-Object {$_.Id -eq 1} | Select -First 10
```
Purpose : Show only Event ID 1 — Process started 

Tracks:
- executed applications
- PowerShell usage
- command-line activity
- attacker tools


SOC use this heavily for:
- malware detection
- suspicious process monitoring
- threat hunting


# Filter Process Termination

Run:

```
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" | Where-Object {$_.Id -eq 5} | Select -First 10
```

Purpose : Shows only Event ID 2 - Process terminated 


# Filter  Network Connections

Run: 

```
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" | Where-Object {$_.Id -eq 3}
```
Purpose:Show network connection events / outbound network connections initiated from the Windows endpoint.

Tracks:
- outbound connections
- suspicious IP communication
- beaconing behavior
- attacker callbacks

 SOC analysts identify:
- Malware communication
- Beaconing activity
- Suspicious outbound traffic investigation
- Reverse shell activity
- Unauthorized external connections


#Filter DNS Query Analysis

```
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" | Where-Object {$_.Id -eq 22}
```
Purpose:DNS query telemetry was generated successfully and captured by Sysmon.

Tracks:
- domain lookups
- suspicious DNS activity
- malware DNS tunneling
- phishing infrastructure

SOC analysts use for:

- Detecting malicious domains
- Investigating phishing activity
- Threat hunting
- Malware infrastructure analysis
- DNS tunneling detection



# Filter Failed Login

Run

```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625}

```
Purposes:Show failed login attempts

Tracks 


SOC Use:
- Password spraying
- brute force detection
- credential attacks



# Filter  Successful Logins

Run
```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4624}
```
Purpose: Show successful logins


# Filter  Process Creation (4688)

Run:

```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4688}
```

Purpose:  Similar to Event ID 1 but from Windows Security logs - Windows process execution.

Tracks:
- what program started
- who started it
- parent process


Soc Analysts use it to detect:
- PowerShell abuse
- Malware execution
- Command-line attacks
- Suspicious parent-child processes
- Show Windows process execution logs


# View Processes

Run:
```
Get-Process
```
Purpose: Show all running processes



# Find Running Services Only

Run:

```
Get-Service | Where-Object {$_.Status -eq "Running"}

```
Purpose:Show only active services


Windows stores security logs called:Event Logs


