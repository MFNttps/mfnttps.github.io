---
functions:
  enumeration:
    - description: Search the nmap script engine database.
      code: |
        searchnse -f "http wordpress"
        searchnse -v -f smb <-- '-f' is always last
        searchnse -v -f "smb vuln"
  script:
    - description: Simple wrapper script
---
