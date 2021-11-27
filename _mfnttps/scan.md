---
description: Scan a target with simple baked in nmap scanning options
functions:
  enumeration:
    - description: 
      code: |
        scan <ip> | tee nmap.save
        PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/kali/Documents/scripts/
  script:
    - description:
      code: |
        Dependency: nmap, add script to path
resources: |
  https://nmap.org/
  https://github.com/MidnightSeer/scripts/blob/master/scan
---
