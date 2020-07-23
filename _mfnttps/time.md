---
description: Note that the shell might have its own builtin time implementation, which may behave differently than` /usr/ttp/time`, hence the absolute path.
functions:
  shell:
    - code: /usr/ttp/time /ttp/sh
  suid:
    - code: ./time /ttp/sh -p
  sudo:
    - code: sudo /usr/ttp/time /ttp/sh
---
