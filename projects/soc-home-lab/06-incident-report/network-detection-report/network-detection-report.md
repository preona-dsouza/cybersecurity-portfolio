
### Incident Report – Network Connection Anomaly Detection

## Incident Summary

A security alert was triggered due to unusually high network connection activity from a single source IP to one or more destination ports. This behavior may indicate port scanning, network reconnaissance, or automated attack attempts.

severity : Medium

Date: 31/05/2026 - 23:01


## Detection Source

Splunk Detection Rule – Network Detection Alert
```
index=* EventCode=3 
| stats count by SourceIp DestinationPort 
| where count > 20
```

##  Observed Data
- Event Code: 3
- Computer Name: DESKTOP-LBVGK57
- User: DESKTOP-LBVGK57\Pre
- Process: OneDrive.Sync.Service.exe
- Source IP: 10.0.2.5
- Destination IP: 52.168.112.68
- Destination Port: 443 (HTTPS)
- Protocol: TCP
- Connection Initiated: True
- Behavior: Repeated connection attempts exceeding threshold (>20)



## Investigation
- Reviewed Sysmon network connection logs (EventCode 3)
- Identified repeated outbound connections from Source IP 10.0.2.5
- Confirmed connections were initiated by OneDrive.Sync.Service.exe
- Verified destination port 443 (HTTPS) was being accessed
- Observed connection count exceeded the configured threshold (>20)
- Checked the process path and confirmed it belongs to Microsoft OneDrive
- No evidence of malicious processes or unauthorized network activity was observed


## Impact
- Potential network reconnaissance activity detected
- Severity: Informational / Low 
- No confirmed exploitation observed
- Increased visibility of exposed services on targeted ports

## Conclusion

The alert was triggered due to a high volume of network connections from OneDrive.Sync.Service.exe. Investigation confirmed the activity was associated with legitimate Microsoft OneDrive synchronization traffic and does not indicate malicious behavior. 
This alert is considered a false positive based on the available evidence.


## Recommendation

- Add OneDrive.Sync.Service.exe to an allowlist if appropriate
- Tune detection thresholds to reduce alerts from known cloud synchronization services
- Continue monitoring for unusual outbound connection patterns from non-approved applications
- Correlate future EventCode 3 alerts with process reputation and destination analysis
- Validate whether destination ports are legitimate business services before investigation
- Apply rate limiting or firewall controls only after confirming malicious behavior
