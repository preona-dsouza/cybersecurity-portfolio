


# Wireshark Notes

## What is Wireshark
Wireshark is a network packet analyzer used to capture and inspect network traffic in real time.

It helps security analysts and network engineers:
- Monitor traffic
- Troubleshoot issues
- Analyze protocols
- Detect suspicious activity
- Investigate incidents

---

# Common Protocols
| Protocol | Purpose                     | Default Port |
|----------|-----------------------------|--------------|
| ICMP     | Connectivity testing        | N/A          |
| DNS      | Domain name resolution      | 53           |
| HTTP     | Web communication           | 80           |
| HTTPS    | Secure web communication    | 443          |
| TCP      | Reliable transport protocol | N/A          |
| UDP      | Fast connectionless protocol| N/A          |



# ICMP 

## Generate ICMP Traffic

```bash
ping google.com
```

## Purpose
- Check connectivity
- Verify host availability
- shows ping traffic

## Packet Types

| Packet       | Meaning      |
|--------------|--------------|
| Echo Request | Ping request |
| Echo Reply   | Ping response|

## Key Learning
ICMP is used for connectivity testing and troubleshooting.


---

# DNS 

## Generate DNS Traffic

```bash
nslookup google.com
```

## Purpose
Resolve domain names into IP addresses.

## Common DNS Records

| Record | Purpose      |
|--------|--------------|
| A      | IPv4 address |
| AAAA   | IPv6 address |
| MX     | Mail server  |
| CNAME  | Alias record |

---

# DNS Troubleshooting

## Check Connectivity

```bash
ping 8.8.8.8
```

If ping works but DNS fails:
- Internet connection works
- DNS issue likely exists

---

## Edit DNS Configuration

```bash
sudo nano /etc/resolv.conf
```
##Purpose:
- Modify DNS server settings


Add:
##replace content with

```text
nameserver 8.8.8.8
nameserver 1.1.1.1
```
## Explanation

| DNS Server | Provider       |
|------------|----------------|
| 8.8.8.8    | Google DNS     |
| 1.1.1.1    | Cloudflare DNS |

##Purpose:
- Configure public DNS servers



---

## Restart NetworkManager

```bash
sudo systemctl restart NetworkManager
```

##Purpose:
- Apply updated DNS settings

---
 

## Outcome
- DNS traffic visible in Wireshark
- Domain resolution functioning normally
- Packet capture successful





## Troubleshooting Steps Performed

| Step | Action                             |
|------|------------------------------------|
| 1    | Verified internet connectivity     |
| 2    | Investigated DNS issue             |
| 3    | Updated DNS servers                |
| 4    | Restarted NetworkManager           |
| 5    | Verified successful DNS resolution |


# HTTP Notes

## Generate HTTP Traffic

```bash
curl http://example.com
```

## What To Observe

| Observation   | Meaning                   |
|---------------|---------------------------|
| GET request   | Client requesting webpage |
| Host header   | Target website            |
| HTTP response | Server response           |

---

# HTTP Methods

| Method | Purpose       |
|--------|---------------|
| GET    | Retrieve data |
| POST   | Send data     |
| PUT    | Update data   |
| DELETE | Remove data   |

---

# Common HTTP Status Codes

| Code| Meaning      |
|-----|--------------|
| 200 | Success      |
| 301 | Redirect     |
| 403 | Forbidden    |
| 404 | Not Found    |
| 500 | Server Error |

---

# TCP Handshake Notes

## Generate TCP Traffic

```bash
telnet google.com 80
```

##Purpose:
- Generate TCP connection traffic

---

# TCP Three-Way Handshake

| Step | Packet  |
|------|---------|
| 1    | SYN     |
| 2    | SYN ACK |
| 3    | ACK     |

---

# SYN ACK Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

Purpose:
- Identify SYN ACK packets
- Observe TCP handshake


## What To Observe

| Packet | Meaning                |
|--------|------------------------|
| SYN    | Connection request     |
| SYN ACK| Server acknowledgment  |
| ACK    | Connection established |


---

# Nmap Detection Notes

## Generate Scan

```bash
nmap 10.0.2.4
```

---

# Detect SYN Scan

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

##Purpose:
- Identify SYN packets
- Detect connection initiation
- Detect potential scans
---

# What To Observe

| Observation          |   Meaning              |
|----------------------|------------------------|
| Multiple SYN packets | Port scanning          |
| Sequential ports     | Reconnaissance activity|



##---Filters

## TCP

```text
tcp
```

Shows TCP packets.

---

## HTTP Requests

```text
http.request
```

Shows only HTTP requests.

---

## Filter by Port

```text
tcp.port == 80
```

Shows traffic on port 80.

---

## Filter by Source IP

```text
ip.src == 10.0.2.15
```

##Purpose:
- Show packets from source IP

---

## Filter by Destination IP

```text
ip.dst == 10.0.2.4
```


##Purpose:
- Show packets to destination IP


---

## Filter by Any IP

```text
ip.addr == 10.0.2.4
```

##Purpose:
- Show traffic involving specified IP


---

## Filter by DNS Port

```text
udp.port == 53
```

Purpose:
- Show DNS traffic

---

## Combined Filter

```text
ip.addr == 10.0.2.4 && tcp.port == 80 && http.request
```

##Purpose:
- Show HTTP requests for specific IP on port 80

---


# Useful Commands

## Open Wireshark

```bash
wireshark
```

---

## Ping Test

```bash
ping google.com
```

---

## DNS Lookup

```bash
nslookup google.com
```

---

## HTTP Request

```bash
curl http://example.com
```

---

## TCP Handshake Test

```bash
telnet google.com 80
```

---

## Nmap Scan

```bash
nmap 10.0.2.4
```

---

# Key Learning

- Wireshark captures and analyzes network packets
- Filters improve traffic analysis
- DNS issues can be isolated through troubleshooting
- HTTP traffic may expose sensitive information
- TCP handshake establishes communication
- Nmap scans are detectable through SYN packet analysis
- Packet analysis supports incident investigation and threat detection

