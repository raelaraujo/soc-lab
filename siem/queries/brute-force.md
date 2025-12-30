# SPLUNK: Detect a brute force in ssh

## Query:
index=linux sourcetype=secure "Failed password"
| stats count by src_ip
| where count > 5

## Explain:
verify in the system log some failed attempts ssh to login
