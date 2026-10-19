


## Attack 3 — Suspicious Process


# Investigate Windows process creation events.


#  Step1 - Process Execution
Run:
```
cmd.exe
powershell.exe
whoami
hostname
ipconfig
ping google.com
nslookup google.com
tasklist
systeminfo

```

# Attackers  performed:

- User discovery (whoami)
- Host discovery (hostname)
- Network discovery (ipconfig, ping google.com, nslookup google.com)
- Process enumeration (tasklist)
- System enumeration (systeminfo)
- Execution environment setup (cmd, powershell)

# Process generated  Generated

| Source           | Event ID | Meaning          |
| ---------------- | -------- | ---------------- |
| Sysmon           | 1        | Process Creation |
| Windows Security | 4688     | Process Creation |




# Evidence - screenshots  -
- process-created.png
- Suspicious-process-sysmon-logs.png
-  Suspicious- process-Sysmon-logs-1.png
- suspicious-Sysmon-logs-4688.png


# SOC Interpretation

The simulated attack activity generated endpoint telemetry across multiple Sysmon event categories.


# SOC Relevance

This investigation demonstrates how SOC analysts identify:
These behaviors are commonly observed during the early stages of attacker reconnaissance and post-compromise enumeration and are frequently investigated within enterprise SOC environments.

 SOC analysts can correlate:

- Powershell execution
- Process execution
- DNS activity
- Network connections
- Authentication events
- External communication


# SOC Skills Demonstrated

- Event correlation
- Endpoint telemetry analysis
- Threat hunting mindset
- Timeline reconstruction
- Security investigation workflow
