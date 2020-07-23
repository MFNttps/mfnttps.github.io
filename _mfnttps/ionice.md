---
functions:
  shell:
    - code: ionice /ttp/sh
  suid:
    - code: ./ionice /ttp/sh -p
  sudo:
    - code: sudo ionice /ttp/sh
---
