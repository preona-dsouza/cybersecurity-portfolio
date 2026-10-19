

## Attack 2 — Failed Login Simulation

Generate failed authentication events.

######### Step 1 — Generate Failed Logins

Lock Windows VM:

Windows + L

Attempt wrong passwords multiple times.


######### step 2 - Event Investigated

Run command on Admin Powershell

```
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625} | Select -First 10

```
######### output- Screenchot - brute-force-attack_Failed Logins.png

Event ID     Meaning
4625         Failed Login Attempt


######### Verify
 
Event Viewer: 
Search:
4625


######### Evidence- screenshot
- brute-force-attack_Failed Logins.png

######### Findings

- Windows Security logs captured failed login attempts successfully.
- Authentication failure events included timestamps and account details.
- Multiple repeated failures were visible in the logs.


######### Soc relevance
SOC analysts monitor Event ID 4625 to detect:

Brute force attacks
Password spraying
Unauthorized access attempts
Account abuse
Credential attacks



