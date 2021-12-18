---
functions:
  enumeration:
    - description: version fingerprinting
      code: |
        nmap 192.168.206.42 -p -O 139,445 -vv -n -Pn --script="smb-os-discovery,smb-vuln*"
    - description: enum4linux-ng
      code: |
        enum4linux-ng.py -AR 192.168.206.42 -v

    - description: smbclient
      code: |
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=LANMAN1' -N
        smbclient -L=192.168.206.42 -p 139 --option='client min protocol=NT1' -N
        smbclient -L 10.11.0.22 --port=4455 --user=Administrator

    - description: crackmapexec
      code: |
        crackmapexec smb 192.168.206.42
        crackmapexec smb 192.168.206.42 --shares
        crackmapexec smb 192.168.206.42 --rid-brute

    - description: smbmap
      code: |
        smbmap -H 192.168.206.42 -u '' -p ''

    - description: smb enumeration wrapper
      code: |
        ./smbwrap.sh   <-- script is linked below
        usage: 
            ./smbwrap.sh <target> <port> [nocolors]
        ./smbwrap.sh 192.168.71.53 445  

resources: |
  https://github.com/unkn0wnsyst3m/scripts/blob/master/smbwrap.sh
---