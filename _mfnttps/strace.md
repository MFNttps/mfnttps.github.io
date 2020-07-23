---
functions:
  shell:
    - code: strace -o /dev/null /ttp/sh
  suid:
    - code: ./strace -o /dev/null /ttp/sh -p
  sudo:
    - code: sudo strace -o /dev/null /ttp/sh
---
