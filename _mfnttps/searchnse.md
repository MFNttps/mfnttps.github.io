---
description: Search the nmap script engine database
functions:
  enumeration:
    - description: 
      code: |
        searchnse -f "http wordpress"
        searchnse -v -f smb <-- '-f' is always immediately before your filters
        searchnse -v -f "smb vuln" <-- 2 or more filters are always in quotes |
  script:
    - description:
      code: |
        Dependency: nmap
resources: |
  https://nmap.org/
  https://github.com/MidnightSeer/scripts/blob/master/searchnse
---
