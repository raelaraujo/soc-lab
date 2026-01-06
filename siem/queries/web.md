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
