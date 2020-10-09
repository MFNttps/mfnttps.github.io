---
functions:
  privilege-escalation:
    - description: |
      Simplistic checklist for linux privilege escalation
      - [ ] whoami
      - [ ] id
        [ ] cat /etc/passwd
        [ ] hostname
        [ ] cat /etc/issue
        [ ] cat /etc/*-release
        [ ] cat /proc/version
        [ ] env
      code: |
        
        sudo -l
        uname -a
        ps aux
        ip a
        ifconfig
        /sbin/route #routel
        netstat -plant
resources: |
      
---
