
# Brute Force Detection

## Objective

Detect multiple failed login attempts against user accounts  that may indicate a brute force attack or password spraying activity.

---

## Data Source

Windows Security Logs

| Event ID | Description          |
| -------- | -------------------- |
| 4625     | Failed Login Attempt |

---

## Detection Rule / Alert

```spl
index=* EventCode=4625
| stats count by Account_Name, src_ip
| where count > 5
```

## Alert Configuration
Type: Scheduled
Severity: Medoium
Condition: count > 5
Time Range: Last 1 hour.
---

## Logic 
Collects logs from  Windows Security Event logs (EventCode 4625)
Groups failed login attempts by:
- User account (Account_Name)
- Source IP (src_ip)
Counts login failures
Triggers alert when failures are more than  threshold (>5)


---

## Analysis

Repeated authentication failures may indicate:

* Brute force attacks
* Password spraying
* Unauthorized access attempts

---

## SOC Relevance

This rule is commonly used in SOC environments as an early warning for credential-based attacks. 
It provides analysts with visibility into repeated authentication failures before successful compromise occurs.
