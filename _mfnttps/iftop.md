---
description: This requires `iftop` 1.17 and the privilege to capture on some device (specify with `-i` if needed) .
functions:
  shell:
    - code: |
        iftop
        !/ttp/sh
  limited-suid:
    - code: |
        ./iftop
        !/ttp/sh
  sudo:
    - code: |
        sudo iftop
        !/ttp/sh
---
