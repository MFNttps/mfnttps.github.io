---
functions:
  enumeration:
    - description: Sniff the wire for samba version information
      code: |
        sudo ngrep -i -d tun0 's.?a.?m.?b.?a.*[[:digit:]]'
---
