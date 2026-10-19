
### Network scan Detection

## Objective
Detect potential port scanning activity by identifying source IP addresses attempting connections to multiple destination ports within a short period of time. In short, Detect excessive network connections that may indicate scanning activityData Source

---

## Data source
Sysmon Network Connection Logs

|Event ID | Description        |
|---------|--------------------|
|3	  | Network Connection |


---

## Detection Rule / Alert
```
index=* EventCode=3
| stats count by SourceIp, DestinationPort
| where count > 20

```

---

## Alert Configuration

Type: real-time

Severity: Medium

Condition: count > 20

---

## Logic
Collects network connection events from Sysmon logs (EventCode 3).
Groups network connection activity by:
 -  Source IP address (SourceIp)
 -  Destination Port (DestinationPort)
Counts the number of connection attempts for each Source IP and Destination Port combination.
Triggers an alert when the connection count exceeds the defined threshold (>20).

---

## Analysis
Repeated connection attempts to destination ports may indicate:

- Port scanning activity
- Network reconnaissance
- Vulnerability discovery attempts
- Malware propagation behavior
- Unauthorized network enumeration

---

## SOC Relevance

This rule provides visibility into potential reconnaissance activities occurring within the environment. 
Port scanning is often an early stage of an attack lifecycle, where adversaries attempt to identify exposed services and potential attack vectors.

---
