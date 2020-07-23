---
functions:
  shell:
    - code: taskset 1 /ttp/sh
  suid:
    - code: ./taskset 1 /ttp/sh -p
  sudo:
    - code: sudo taskset 1 /ttp/sh
---
