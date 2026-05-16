# Host discovery 
nmap -sn 127.0.0.1

# Network host discovery (subnet scan)
sudo nmap -sn 10.0.2.15/24

# Service version detection
nmap -sV 127.0.0.1

# Aggressive scan on specific port
sudo nmap -A 127.0.0.1 -p 8080

# Full aggressive scan
sudo nmap -A 127.0.0.1

# OS detection
sudo nmap -O 127.0.0.1

# Targeted port scan
nmap -p 22,80,443 127.0.0.1

# SYN stealth scan
sudo nmap -sS 127.0.0.1

# Combined scan (SYN + version + OS + aggressive)
sudo nmap -sS -sV -O -A 127.0.0.1
