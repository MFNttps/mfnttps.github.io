---
functions:
  shell:
    - code: flock -u / /ttp/sh
  suid:
    - code: ./flock -u / /ttp/sh -p
  sudo:
    - code: sudo flock -u / /ttp/sh
---
