# Wireshark Packet Analysis Lab

## Objective
This lab demonstrates practical packet analysis and network troubleshooting using Wireshark.

The lab covers:
- ICMP analysis
- DNS traffic analysis
- HTTP traffic analysis
- TCP handshake analysis
- Wireshark Packet filtering
- Nmap scan detection
- Network troubleshooting
- Reconnaissance detection

---

# Objectives

- Capture and analyze network packets
- Understand common protocols
- Practice Wireshark filters
- Investigate DNS resolution issues
- Analyze HTTP communication
- Observe TCP three-way handshake
- Detect reconnaissance activity



# Tools Used

| Tool       | Purpose              |
|------------|----------------------|
| Wireshark  | Packet analysis      |
| Kali Linux | Analysis machine     |
| Nmap       | Network scanning     |
| curl       | Generate HTTP traffic|
| ping       | Connectivity testing |
| nslookup   | DNS testing          |
| telnet     | TCP handshake testing|

---

# Start Wireshark

## Command

```bash
wireshark
```

## Steps
1. Open Wireshark
2. Select active interface
3. Start packet capture

---

# ICMP Analysis

## Generate ICMP Traffic

```bash
ping google.com
```

## Wireshark Filter

```text
icmp
```

## Key Learning
Shows ping traffic.
ICMP is used for connectivity testing and troubleshooting.


---

# DNS Analysis

## Generate DNS Traffic

```bash
nslookup google.com
```

## Wireshark Filter

```text
dns
```

## Key Learning
Shows DNS queries and responses.

---

# Network Troubleshooting

Investigated DNS resolution issue.

## Problem
DNS traffic was not appearing or domain resolution failed.

---

# Step 1 — Check Connectivity

## Command

```bash
ping 8.8.8.8
```

## Purpose
Verify internet connectivity independent of DNS.

## Result
Internet connectivity was working.

This indicated:
- Network connection OK
- DNS configuration issue likely

---

# Step 2 — Edit DNS Configuration

## Command

```bash
sudo nano /etc/resolv.conf
```

## Replace Content With

```text
nameserver 8.8.8.8
nameserver 1.1.1.1
```
##Purpose
- Configure public DNS servers

---

# Step 3 — Restart Network Manager

## Command

```bash
sudo systemctl restart NetworkManager
```

## Purpose
Apply updated DNS settings.

---

# Verification

## Command


```bash
nslookup google.com
```

## Result
DNS resolution successful.

Wireshark began displaying DNS traffic correctly.


---

# HTTP Analysis

## Generate HTTP Traffic

``` open browser and search google.com```

```bash
curl http://example.com
```
#Purpose
- Generate HTTP GET requests

## Wireshark Filter

```text
http
```
##Purpose
-Display HTTP traffic only



---

# Follow HTTP Stream

## Steps
1. Right-click HTTP packet
2. Follow
3. TCP Stream

## Purpose
View full HTTP conversation.

---

# TCP Handshake Analysis

## Generate TCP Traffic

```bash
telnet google.com 80
```

##Purpose:
- Generate TCP connection traffic


## Wireshark Filter

```text
tcp
```

##Purpose:
- Display TCP traffic only


---

# SYN ACK Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

## Purpose:
- Identify SYN ACK packets
- Observe TCP handshake
---

# Filters

# Filter by IP

```text
ip.addr == 10.0.2.4
```

---

# HTTP Requests Only

```text
http.request
```

---

# Port 80 Traffic

```text
tcp.port == 80
```

---

# Combined Filter

```text
ip.addr == 10.0.2.4 && tcp.port == 80 && http.request
```

## Purpose
Filter:
- Specific IP
- Port 80 traffic
- HTTP requests only

---

# Nmap Scan Detection

## Generate Scan

```bash
nmap 10.0.2.4
```

## Detection Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

## Purpose:
- Identify SYN packets
- Detect connection initiation
- Detect potential scans


## Key Learning
Wireshark can detect reconnaissance behavior such as Nmap scans.


---
# Key Takeaways

- Packet analysis  provides forensic visibility
- Wireshark enables deep packet inspection
- Network troubleshooting: DNS issues can be isolated through troubleshooting
- HTTP traffic is visible in plaintext,  can expose sensitive information
- TCP handshake establishes reliable communication
- Packet filters improve investigation efficiency
- Reconnaissance activity is detectable through packet analysis
- Structured documentation improves cybersecurity investigations





