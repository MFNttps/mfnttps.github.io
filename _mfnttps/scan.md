---
description: Scan a target with simple baked in nmap scanning options
functions:
  enumeration:
    - description: 
      code: |
        scan <ip> (saves to $ip.nmap.save)
        scan <ip>-<ip> (saves to $ip.nmap.save)
  script:
    - description:
      code: |
        Dependency: nmap, add script to path
resources: |
  https://nmap.org/
  https://github.com/MidnightSeer/scripts/blob/master/scan
---
