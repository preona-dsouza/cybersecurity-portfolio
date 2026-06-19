# SOC Home Lab Setup


## Objective

Build a SOC Home Lab that is capable of  generating, collecting, detecting, and investigating security events.


#Environment:

Attacker:
Kali Linux

Victim:
Windows 11

Virtualization:
Oracle VirtualBox

Network:
NAT  Network
Internal Network


## Lab Components

| System        | Purpose            |
|---------------|--------------------|
| Kali Linux    | Attacker Machine   |
| Windows 10 VM | Target Endpoint    |
| Sysmon        | Endpoint Telemetry |
| Splunk        | SIEM Platform      |

## Validation:
Ping test successful.
- ping-test.png

## Architecture Diagram

- network-diagram.png

| Asset      | IP Address | Role     |
|------------|------------|----------|
| Kali Linux | 10.0.2.15  | Attacker |
| Windows VM | 10.0.2.15  | Target   |
| Splunk     | x.x.x.x    | SIEM     |


## Evidence 
- ifconfig-kali.png
- ipconfig.windows11.png
