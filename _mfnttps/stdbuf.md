---
functions:
  shell:
    - code: stdbuf -i0 /ttp/sh
  suid:
    - code: ./stdbuf -i0 /ttp/sh -p
  sudo:
    - code: sudo stdbuf -i0 /ttp/sh
---
