
### Dashboard
Designed a SOC monitoring dashboard in Splunk to visualize authentication activity, PowerShell execution, DNS telemetry, network connections, and endpoint process creation using Sysmon and Windows Security Logs.

## Panel 1 — Failed Login Attempt 

# Query
EventCode=4625
| timechart count

# Visualization
Area Chart

# SOC Relavance
Detect:
Brute force attacks
Password spraying
Unauthorized login attempts



# Panel 2 —  Error in the last 24 hours

# Query
error OR failed OR severe OR ( sourcetype=access_* ( 404 OR 500 OR 503 ) )

# Visualization
Line chart

# SOC relevance
Highlight application, system, and web server errors to quickly identify operational issues, service disruptions, or potential security incidents. 



## Panel 3  — PowerShell Activity

# Query
EventCode=4688
powershell

# Visualization
Table

# SOC Relevance
Detect PowerShell abuse.



##  Panel 4 — DNS Queries

# Query
EventCode=22
| stats count by QueryName

# Visualization
Table

# SOC Relavance
- Monitor DNS activity.
- Detect:
   - Suspicious domains
   - Malware communication



## Panel 5 — Event Volume by Event Code

# Query
index=*
| stats count by EventCode


# Visualization
Pie Chart

# SOC Relevance
Provide an overview of event volume by event type to understand log composition and identify dominant or unexpected activity patterns.




## Panel 6 - Process Activity

# Query
EventCode=1
| stats count by Image

# Visualization
Statisics  Table

# SOC Revalance
Identify the most frequently executed processes and detect unusual or excessive process activity.


