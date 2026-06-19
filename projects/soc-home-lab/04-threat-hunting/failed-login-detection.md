

# Authentication Failure Investigation


## Objective

Investigate failed authentication activity.


##  Generated Failed Logins

Lock Windows:Windows + L

Enter wrong passwords multiple times.

## Search Query -Search Failed Logins


## Windows Verification

### Query

```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625}
```


## Splunk Investigation

### Search Query

```spl
EventCode=4625

```

### Event Investigated
Event ID 4625 indicates a failed authentication attempt.


| Event ID  | Description          |
|-----------|----------------------|
| 4625      | Failed Login Attempt |

### Evidence

- windows-event-4625.png

- splunk-eventcode-4625.png

---

##Findings
Observed multiple failed logins targeting local accounts.

##Potential causes:
- User error
- Password spraying
- Brute force attack


##SOC Relevance
Repeated authentication failures are often early indicators of credential attacks.

Soc Investigation:
- repeated failures
- usernames
- timestamps
- suspicious patterns

