# Findings

## ICMP Analysis

### Observation
ICMP Echo Request and Echo Reply packets were successfully captured.

### Result
Connectivity between systems was verified.

### Key Learning
ICMP traffic is commonly used for:
- Connectivity testing
- Network troubleshooting
- Host availability verification

## DNS Analysis

###Oberservation
-Initial DNS traffic was not visible and domain resolution failed.
-Investigation Performed
- Network connection operational
- DNS configuration issue suspected
-Edited DNS configuration
-Restart Network Services 

###Result
- DNS resolution successfully restored.
- DNS packets visible in Wireshark
- Observed successful DNS queries to google.com
- DNS responses returned IPv4 addresses



## HTTP Analysis

###Observed
- HTTP traffic visible in plaintext
-HTTP traffic was successfully captured.
- GET requests,Host headers,HTTP responses  successfully identified

###Result
HTTP traffic is transmitted in plaintext and may expose sensitive information.

## TCP Handshake

## Observatio
-TCP three-way handshake packets successfully identified.
- SYN → SYN ACK → ACK sequence observed

###Result
TCP handshake establishes reliable communication between systems.


## Nmap Detection

###Observed
- Multiple SYN packets detected
- Sequential port access identified
-Large numbers of SYN packets observed targeting multiple ports.
- Possible reconnaissance activity observed

###Result
Behavior consistent with reconnaissance or port scanning activity.

### Wireshark Filters

###Result
Filters reduce noise and improve investigation efficiency.


# Overall Learning Outcomes

- Performed packet capture and protocol analysis
- Troubleshooted DNS configuration issues
- Investigated HTTP communication
- Observed TCP connection establishment
- Practiced advanced Wireshark filtering
- Detected reconnaissance traffic patterns
- Improved understanding of network protocols and analysis workflows



---
