# Nmap Scanning Lab

## Objective
Perform network reconnaissance and service enumeration using Nmap.

---

## Tools Used
- Kali Linux
- Nmap

## Environment
- Kali Linux VM
- Localhost testing environment
- Python HTTP Server
- OpenSSH Server


---

## Lab Activities
- Host discovery
- Port scanning
- Service version detection
- OS fingerprinting
- Aggressive scanning
-SYN stealth scan
-Full recon scan
---

## Commands Used

### Ping Scan
```bash
nmap -sn 10.0.2.0/24
```

### Service Detection 
```bash
nmap -sV 127.0.0.1 
```


### Service Detection port 8080
```bash
nmap -sV 127.0.0.1 -p 8080
```


### OS detetctio  Scan
```bash
sudo nmap -O 127.0.0.1 
```


### Aggressive Scan
```bash
sudo nmap -A 127.0.0.1 -p 8080
```

### full recon Scan
```bash
sudo nmap -sS -sV -O -A 127.0.0.1
```


---

## Key Findings

- Identified active hosts on the local network
-Detected open ports and services
- Detected open HTTP service on port 8080
- Performed service version enumeration 
- Service detection helps identify exposed applications and versions.
-- OS detected as Linux (Debian), based on Nmap fingerprinting(no exact match)
- Learned reconnaissance techniques 

---

## Screenshots
Stored in screenshots folder.

---

## Skills Learned
- Network reconnaissance
- Basic network analysis
- Attack surface analysis
- Performed host discovery and subnet scanning using Nmap
- Identified open ports and running services
- Conducted service version and OS detection
- Executed SYN stealth and aggressive scans
- Analyzed exposed services and basic security misconfigurations

