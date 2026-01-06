# Default spl queries 

## q1:
index=web sourcetype="access_combined"
| stats count

## q2:
index=web sourcetype="access_combined"
| status count by status

see and enumerate the http sattus code
