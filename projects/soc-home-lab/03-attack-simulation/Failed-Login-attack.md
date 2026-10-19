

## Attack 2 — Failed Login Simulation

### Step 1 — Generate Failed Logins

Lock Windows VM:

Windows + L

Attempt wrong passwords multiple times.


### Step 2 — Event Investigated


Run command on Admin Powershell

```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625} | Select -First 10

```
### Output — Screenshot: brute-force-attack_Failed Logins.png

### Verify

Event ID | Meaning
--- | ---
4625 | Failed Login Attempt

In Event Viewer, search for event ID `4625`.


### Evidence — Screenshot
- brute-force-attack_Failed Logins.png

### Findings

- Windows Security logs captured failed login attempts successfully.
- Authentication failure events included timestamps and account details.
- Multiple repeated failures were visible in the logs.


### SOC Relevance
SOC analysts monitor Event ID 4625 to detect:

Brute force attacks
Password spraying
Unauthorized access attempts
Account abuse
Credential attacks
