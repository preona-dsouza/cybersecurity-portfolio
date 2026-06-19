

# DNS & Network Activity Investigation


## Objective

To simulate and investigate DNS resolution and network communication activity on a Windows endpoint using Sysmon logs and Splunk, and understand how SOC analysts detect external communication behavior.



##  Process Steps

### Step 1 — Generate DNS Activity

Run the following commands on the Windows machine:

```powershell
nslookup google.com
nslookup microsoft.com
```

---

### Step 2 — Generate Network Activity

Run the following commands:

```powershell
ping google.com
curl https://google.com
```

These commands generate network connections and outbound communication attempts.

---

## Events Generated

| Activity Type      | Sysmon Event ID | Description                 |
|--------------------|-----------------|-----------------------------|
| DNS Query          | 22              | DNS resolution activity     |
| Network Connection | 3               | Outbound network connection |

---



##  Output Evidence

- dns-network-process.png 
- sysmon-dns-results.png
- sysmon-network-results.png 
---

##  Findings

- DNS queries for `google.com` and `microsoft.com` were successfully captured.
- Network connection events were generated during `ping` and `curl` execution.


##  SOC Relevance

This activity is important for SOC analysts because:

- DNS queries can reveal malicious domains or C2 communication
- Network connections help detect data exfiltration attempts
- Repeated DNS + network patterns may indicate beaconing behavior
- Tools like `curl` are often used in post-exploitation activity

SOC teams monitor:

- Suspicious external connections
- Unknown domain lookups
- Unusual outbound traffic patterns
- Malware communication channels

---


