---
functions:
  enumeration:
    - description: RPC enumeration on Windows
      code: |
        rpcdump.py 10.10.10.204  [pip3 install impacket]
        rpcclient -p 135 -N 10.10.10.204
        rpcclient -W WORKGROUP -U % 192.168.206.42 --option='client min protocol=LANMAN1'
        rpcclient -W WORKGROUP -U % 192.168.206.42 --option='client min protocol=NT1'
---
