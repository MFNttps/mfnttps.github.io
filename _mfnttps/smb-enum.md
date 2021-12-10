---
functions:
  enumeration:
    - description: version fingerprinting
      code: |
        nmap 192.168.206.42 -p -O 139,445 -vv -n -Pn --script="smb-os-discovery,smb-vuln\*"

    - description: smbclient
      code: |
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=LANMAN1' -N
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=NT1' -N
        smbclient -L 10.11.0.22 --port=4455 --user=Administrator

    - description: crackmapexec
      code: |
        crackmapexec smb 192.168.206.42
---