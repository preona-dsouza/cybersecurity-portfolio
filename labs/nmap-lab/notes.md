What is Nmap?

Nmap (Network Mapper) is a network reconnaissance and security auditing tool(scanning tool) used for:

Discovering hosts on a network
Finding open ports
Detecting services and versions
Identifying operating systems
Security auditing and reconnaissance


# Common Nmap Commands


# Nmap Notes

## What is Nmap?
Nmap (Network Mapper) is a network reconnaissance and security auditing tool used to discover hosts, open ports, running services, and operating systems.

---

# Common Nmap Commands


## Basic Port Scan
```bash
nmap 127.0.0.1
```
(can be local or target machine)
Purpose:
- Scan top 1000 TCP ports
- Identify open ports


---

## Scan Multiple Hosts
```bash
nmap 192.168.1.10 192.168.1.20
```

Purpose:
- Scan multiple specific hosts
- Identify open ports on selected systems

---

## Scan Hosts in Range
```bash
nmap 192.168.1.1-50
```

Purpose:
- Scan hosts within an IP range
- Discover active devices on the network

---

## Scan Entire Subnet
```bash
nmap 192.168.1.0/24
```

Purpose:
- Scan all hosts in a subnet
- Discover systems on the network

---

## Host Discovery (Ping Scan)
```bash
nmap -sn 10.0.2.0/24
```

Purpose:
- Discover active hosts on the network
- No port scanning performed
---


## Service Version Detection
```bash
nmap -sV 127.0.0.1
```

Purpose:
- Detect running services
- Enumerate service versions

---

## OS Detection
```bash
sudo nmap -O 127.0.0.1
```

Purpose:
- Attempt operating system fingerprinting

---

## Aggressive Scan
```bash
sudo nmap -A 127.0.0.1
```

Purpose:
- OS detection
- Version detection
- Script scanning
- Traceroute

---

## SYN Stealth Scan
```bash
sudo nmap -sS 127.0.0.1
```

Purpose:
- Perform stealth TCP SYN scanning

---

## Full Port Scan
```bash
nmap -p- target
```

Purpose:
- Scan all 65535 ports
- Discover hidden services

---


## Scan Specific Ports
```bash
nmap -p 22,80,443,8080 127.0.0.1
```

Purpose:
- Scan selected ports only

---

## Save Scan Results
```bash
nmap -sV 127.0.0.1 -oN scan-results.txt
```

Purpose:
- Save scan output to a file

---

# Important Ports

| Port | Service |
|---|---|
| 21 | FTP |
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 8080 | Alternate HTTP |

---

# Key Concepts

## Reconnaissance
The process of gathering information about a target system or network.

## Enumeration
Extracting detailed information about services, versions, and systems.

## Attack Surface
The exposed entry points that attackers may attempt to exploit.

## Service Enumeration
Identifying services running on open ports.

## Banner Grabbing
Collecting service/version information from exposed services.

---


# Security Relevance

- Open ports may expose services to attackers
- Service versions can reveal vulnerabilities
- Reconnaissance is commonly used during penetration testing and threat analysis
- Exposed directory listings may leak sensitive information

--- --- --- 
