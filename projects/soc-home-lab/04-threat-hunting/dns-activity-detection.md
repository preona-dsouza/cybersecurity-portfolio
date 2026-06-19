Investigation 3 — DNS Activity Analysis

## Objective

Investigate DNS query activity captured by Sysmon.

---

## Activity Generated

```powershell
nslookup google.com
nslookup microsoft.com
```

---

## Sysmon Verification

### Query

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" |
Where-Object {$_.Id -eq 22}
```

---

## Splunk Investigation

### Search Query

```spl
EventCode=22



### Event Investigated

| Event ID  | Description |
|-----------|-------------|
| 22        | DNS Query   |

### Evidence

- sysmon-event-22.png
- splunk-eventcode-22.png

---

## Findings

DNS resolution activity was successfully recorded.

Observed domains:

- google.com
- microsoft.com

---

## Security Analysis

DNS telemetry is highly valuable for identifying:

- Malware communications
- Phishing domains
- Command and Control infrastructure
- DNS tunneling activity

---
