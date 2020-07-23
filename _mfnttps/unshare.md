---
functions:
  shell:
    - code: unshare /ttp/sh
  suid:
    - code: ./unshare -r /ttp/sh
  sudo:
    - code: sudo unshare /ttp/sh
---
