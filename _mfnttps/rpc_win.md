---
functions:
  enumeration:
    - description: RPC enumeration on Windows
      code: |
        rpcdump.py 10.10.10.204  [pip3 install impacket]
        rpcclient -p 135 -N 10.10.10.204
---
