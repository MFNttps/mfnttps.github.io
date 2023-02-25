---
functions:
  enumeration:
    - description: dnsenum
      code: |
        dnsenum hutch.offsec --dnsserver 192.168.165.122

    - description: fierce
      code: |
        fierce --domain hutch.offsec --dns-servers 192.168.165.122

    - description: adidnsdump
      code: |
        pip install git+https://github.com/dirkjanm/adidnsdump#egg=adidnsdump
        adidnsdump -u icorp\\testuser --print-zones icorp-dc.internal.corp
        adidnsdump -u icorp\\testuser --print-zones icorp-dc.internal.corp --print-zones
resources: |
  https://dirkjanm.io/getting-in-the-zone-dumping-active-directory-dns-with-adidnsdump/
  https://github.com/dirkjanm/adidnsdump
---