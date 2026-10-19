
# Incident Report – Brute Force Authentication Attempts

##  Incident Summary

A security alert was triggered due to multiple failed login attempts against a user account. The activity is  potential brute force or password spraying attempts targeting Windows system authentication.

severity - Medium

Date- 31/05/2026 18:27 

---

##  Detection Source

Splunk Detection Rule – Brute Force Alert

```
index=* EventCode=4625 
| stats count by Account_Name, src_ip 
| where count > 5
```

## Observed Data
Multiple failed authentication attempts recorded
Event Code: 4625 (Failed Logon)
Computer Name: DESKTOP-LBVGK57
Account: Pre
Logon Type: 2 (Interactive logon)
Failure Reason: Unknown user name or bad password
Status: 0xC000006D
Sub Status: 0xC000006A
Source IP: 127.0.0.1 (local host)
Caller Process: svchost.exe
Authentication Package: Negotiate

## Investigation 
- Reviewed Windows Security logs for failed authentication attempts (EventCode 4625)
- Identified repeated logon failure for local user account Pre
- Confirmed logon type is interactive (type 2), indicating local login attempt
- Source IP is loopback (127.0.0.1), indicating local system-originated authentication
- Caller process svchost.exe suggests system service or local authentication subsystem
- No evidence of external network-based authentication attempt
- Failure reason indicates incorrect username or password

## Impact
- Suspicious authentication behavior detected
- No evidence of external brute force attack
- Potential local credential misentry or application-level authentication failure
- Possible misconfigured service or background process attempting authentication
- Low immediate security impact, but may indicate local misconfiguration or user account issue

## Conclusion
The activity does not show external attack behavior and is most likely related to a misconfigured service or incorrect credential usage on the host.
The alert successfully identified multiple failed login attempts and flagged potential brute force activity.


## Recommendation
- Verify if user Pre is a valid and actively used account 
- Monitor repeated  authentication attempts from same account and source Ip 
- Check scheduled tasks, services, or applications using stored credentials
- Investigate svchost.exe service context to identify authentication source
- Review local login policies and credential configurations
- Monitor for repeated 4625 failures to detect potential brute force escalation
- Ensure unused or test accounts are disabled or removed
- Implement  account lockout policies  if repeated failures persist oe temporarily lock the account if unauthorized access is suspected

