---
functions:
  enumeration:
    - description: Search the nmap script engine database.
      code: |
        searchnse -f "http wordpress"
        searchnse -v -f smb <-- '-f' is always immediately before your filters
        searchnse -v -f "smb vuln" <-- 2 or more filters are always in quotes
  script:
    - description: Simple wrapper script
      code: |
        Dependency: nmap
      link: | https://nmap.org/
---
