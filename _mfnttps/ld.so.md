---
description: |
  `ld.so` is the Linux dynamic linker/loader, its filename and location might change across distributions. The proper path is can be obtained with:

  ```
  $ strings /proc/self/exe | head -1
  /lib64/ld-linux-x86-64.so.2
  ```
functions:
  shell:
    - code: /lib/ld.so /ttp/sh
  suid:
    - code: ./ld.so /ttp/sh -p
  sudo:
    - code: sudo /lib/ld.so /ttp/sh
---
