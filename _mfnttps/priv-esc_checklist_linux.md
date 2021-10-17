---
functions:
  privilege-escalation:
    - description: Simplistic and standard checklist for linux privilege escalation, in no particular order
      code: |
        Feel free to copy paste the entire listing below
        Standard:
        - [ ] whoami
        - [ ] id
        - [ ] cat /etc/passwd
        - [ ] cat /etc/group
        - [ ] hostname
        - [ ] cat /etc/issue
        - [ ] cat /etc/*-release
        - [ ] cat /proc/version
        - [ ] lsb_release -a
        - [ ] env
        - [ ] sudo -l
        - [ ] uname -a
        - [ ] ps aux
        - [ ] ip a
        - [ ] ifconfig
        - [ ] /sbin/route
        - [ ] netstat -plant
        - [ ] cat /etc/crontab
        - [ ] grep "CRON" /var/log/cron.log
        - [ ] dpkg -l
        - [ ] mount
        - [ ] cat /etc/fstab
        - [ ] ssh -V
        - [ ] /bin/lsblk
        - [ ] lsmod
        - [ ] echo $PATH

        File Permission Searching:
        - [ ] find / -type f -perm -2 2>/dev/null | grep -v "^/proc/"                     #world writable
        - [ ] find / -user root -perm -002 -type f 2>/dev/null | grep -v "^/proc/"     #world writable ownd by root
        - [ ] ls -al $(find / -perm -1000 -type d 2>/dev/null)   # Sticky bit - Only the owner of the directory or the owner of a file can delete or rename here.
        - [ ] ls -al $(find / -perm -g=s -type f 2>/dev/null)    # SGID (chmod 2000) - run as the group, not the user who started it.
        - [ ] ls -al $(find / -perm -u=s -type f 2>/dev/null)    # SUID (chmod 4000) - run as the owner, not the user who started it.
        - [ ] for file in $(find / -perm -u=s -type f 2>/dev/null ); do ls -al $file; done;
        - [ ] find / -xdev -user root -perm -o+w -type f 2>/dev/null
        - [ ] find / -xdev -group admin -perm -o+w -type f 2>/dev/null
        - [ ] find / -perm -u=s -type f -exec "ls -al {}" \; 2>/dev/null
        - [ ] ls -al /etc/iptables/* -R
        - [ ] ls -lah /etc/cron*        

        MONITOR PROCESSES:
        ------------------
        #!/bin/bash
        IFS=$'\n'
        old_process=$(ps aux --forest | grep -v "ps aux --forest" | grep -v "sleep 1" | grep -v $0)
        while true; do
          new_process=$(ps aux --forest | grep -v "ps aux --forest" | grep -v "sleep 1" | grep -v $0)
          diff <(echo "$old_process") <(echo "$new_process") | grep [\<\>]
          sleep 1
          old_process=$new_process
        done

resources: |
  https://github.com/jondonas/linux-exploit-suggester-2/blob/master/linux-exploit-suggester-2.pl
---

