


Successful Login Investigation


## Purpose
Track successful user authentication events.



## Event ID 4624 — Successful Logins

Sysmon  Search

```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4624}
```

In splunk:
```
EventCode=4624
```

## Event Description
Event ID 4624 indicates a successfull authentication.

| Event code     | Meaning           |
| -------------- | ----------------- |
| 4624           | successful login  |


## Findings
- Successfully authenticated users observed.
- Correlated successful logins with failed login events.


## SOC Relevance
Used for:
- login investigations
- account monitoring
- suspicious user activity

Comparing successful and failed logins helps identify account compromise.





