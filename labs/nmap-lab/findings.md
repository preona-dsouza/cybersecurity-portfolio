# Findings

## Open Services Identified
- Port 22 — SSH (used for remote login)
- Port 80 — Website (Apache web server)
- Port 8080 — Python web server (shows file list)
- Port 443 — Closed (no HTTPS)

---

## Service Results
- SSH service identified as OpenSSH running on Debian Linux
- Apache web server hosting default  page
- Python SimpleHTTPServer exposing directory listing on port 8080
- HTTP headers revealed server versions for both Apache and Python HTTP server - server versions are visible.
---

## OS & Network Findings
- System is Linux (Debian)
- OS detection detected  Linux fingerprinting (no exact match)
- Scan was done on localhost (same machine)

---

## Security Meaning
- Multiple open ports mean more entry points
- Software versions are visible (helps attackers)
- Directory listing can expose files
- No HTTPS means no secure web traffic
- Default settings mean system is not fully secured
