---
functions:
  enumeration:
    - description: smbclient: Enumerate smb/samba shares
      code: |
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=LANMAN1' -N
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=NT1' -N
    - description: crackmapexec: Enumerate smb/samba shares
      code: |
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=LANMAN1' -N
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=NT1' -N
---