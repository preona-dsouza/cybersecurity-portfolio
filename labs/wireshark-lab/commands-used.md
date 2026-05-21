

# Commands and Filters Used

## Wireshark

### Open Wireshark

```bash
wireshark
```

Purpose:
- Start packet capture and analysis

---

# ICMP Analysis

## Generate ICMP Traffic

```bash
ping google.com
```

Purpose:
- Test connectivity
- Generate ICMP packets

---

## Wireshark ICMP Filter

```text
icmp
```

Purpose:
- Display only ICMP traffic

---

# DNS Analysis

## Generate DNS Traffic

```bash
nslookup google.com
```

Purpose:
- Generate DNS queries and responses

---

## Wireshark DNS Filter

```text
dns
```

Purpose:
- Display only DNS packets

---

## DNS Query Filter

```text
dns.flags.response == 0
```

Purpose:
- Show only DNS requests

---

## DNS Response Filter

```text
dns.flags.response == 1
```

Purpose:
- Show only DNS responses

---

# Network Troubleshooting

## Connectivity Check

```bash
ping 8.8.8.8
```

Purpose:
- Verify internet connectivity

---

## Edit DNS Configuration

```bash
sudo nano /etc/resolv.conf
```

Purpose:
- Modify DNS server settings

---

## DNS Servers Added

```text
nameserver 8.8.8.8
nameserver 1.1.1.1
```

Purpose:
- Configure public DNS servers

---

## Restart NetworkManager

```bash
sudo systemctl restart NetworkManager
```

Purpose:
- Apply updated DNS settings

---

# HTTP Analysis

## Generate HTTP Traffic

```bash
curl http://example.com
```

Purpose:
- Generate HTTP GET requests

---

## Wireshark HTTP Filter

```text
http
```

Purpose:
- Display HTTP traffic only

---

## HTTP Requests Filter

```text
http.request
```

Purpose:
- Show only HTTP requests

---

## HTTP Responses Filter

```text
http.response
```

Purpose:
- Show only HTTP responses

---

# TCP Handshake Analysis

## Generate TCP Traffic

```bash
telnet google.com 80
```

Purpose:
- Generate TCP connection traffic

---

## Wireshark TCP Filter

```text
tcp
```

Purpose:
- Display TCP traffic only

---

## SYN Packet Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

Purpose:
- Identify SYN packets
- Detect connection initiation
- Detect potential scans

---

## SYN ACK Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 1
```

Purpose:
- Identify SYN ACK packets
- Observe TCP handshake

---

## ACK Filter

```text
tcp.flags.ack == 1
```

Purpose:
- Display ACK packets

---




# Nmap Scan Detection

## Generate Nmap Scan

```bash
nmap 10.0.2.4
```

Purpose:
- Perform port scan
- Generate reconnaissance traffic

---

## Nmap Detection Filter

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

Purpose:
- Detect SYN scan activity
- Identify reconnaissance behavior


---


# Filter 

## Filter by IP Address

```text
ip.addr == 10.0.2.4
```

Purpose:
- Show traffic involving specified IP

---

## Filter by Source IP

```text
ip.src == 10.0.2.15
```

Purpose:
- Show packets from source IP

---

## Filter by Destination IP

```text
ip.dst == 10.0.2.4
```

Purpose:
- Show packets to destination IP

---

## Filter by Port 80

```text
tcp.port == 80
```

Purpose:
- Show HTTP port traffic

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

Purpose:
- Show HTTP requests for specific IP on port 80

---


