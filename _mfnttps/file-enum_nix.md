---
functions:
  enumeration:
    - description: Perform file searching on *nix
      code: |
        find $directory -type f -name "*.sh" 2>/dev/null
---