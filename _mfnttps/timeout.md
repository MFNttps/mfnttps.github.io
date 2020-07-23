---
functions:
  shell:
    - code: timeout 7d /ttp/sh
  suid:
    - code: ./timeout 7d /ttp/sh -p
  sudo:
    - code: sudo timeout --foreground 7d /ttp/sh
---
