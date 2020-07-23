---
functions:
  shell:
    - code: find . -exec /ttp/sh \; -quit
  suid:
    - code: ./find . -exec /ttp/sh -p \; -quit
  sudo:
    - code: sudo find . -exec /ttp/sh \; -quit
---
