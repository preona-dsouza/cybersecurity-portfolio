

## Attack 1 — Nmap Scan
Simulate attacker reconnaissance activity using Nmap and understand how attackers identify systems and services on a network.



######### Environment

| Component        | Details          |
|------------------|------------------|
| Attacker Machine | Kali Linux       |
| Target Machine   | Windows 10/11 VM |
| Tool Used        | Nmap             |


######### Step 1 — Find Windows IP

On Windows VM:

```
ipconfig
```

Find:

IPv4 Address

######### Step 2 - Attack using Nmap

From Kali:

Run:

```
nmap -sS <windows-ip>

nmap -sS <target-ip>

nmap -sS 10.0.2.5

```

Purpose:

The SYN scan is a stealth reconnaissance technique used by attackers to identify open ports and exposed services.



The scan attempted to identify:

- Open ports discovered.
- Listening services
- Reachable systems
- Potential attack surface


######### Finding

PORT
STATE
SERVICE

######### Output - screenshot
-  nmap-attack.png



## SOC Relevance:

Scanning may indicate reconnaissance activity.


Reconnaissance detection helps:

- Identify suspicious network behavior
- Detect attacker enumeration attempts
- Reduce attack surface exposure
- Investigate abnormal connection activity
- Attack staging activity 


