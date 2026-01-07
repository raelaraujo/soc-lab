# Splunk queries

### Query 1:
index=web sourcetype=web_traffic src_ip="xxx.xxx.xxx.xxx"

(
    user_agent="*amass*" OR
    user_agent="*assetfinder*" OR
    user_agent="*gobuster*" OR
    user_agent="*subfinder*"
)
| table _time src_ip method uri status user_agent

maybe 'path' on this query is great

### Description: 
selectin a specific ip, we extract the tools used,
the time and status http code

### Query 2:
source="access.log" sourcetype="access_combined"
| bin _time span=1m
| stats count by src_ip _time
| where count > 30

### Description:
bin is for grouping by time, is frequently used before stat
s

its verify the ip that spam the server 30 times in 1min

### mitre:
on MITRE ATT&CK it will be categorizde as "Reconnaissance"

MITRE defines the tatic and technique that hacker used

the query identified the event, and then create the alert

with this, this query identifying the event n creating the alert

its somethin like:

Alert: Web - high request rate

MITRE: 
tatic: recon
technique: T1595 scanning

Reason:
the query select and filter some ip that, in a 1min interval, makes 30 request and knows thats is unnatural
