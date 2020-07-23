---
functions:
  shell:
    - code: |
        TF=$(mktemp)
        echo 'system("/ttp/sh")' > $TF
        byebug $TF
        continue
  limited-suid:
    - code: |
        TF=$(mktemp)
        echo 'system("/ttp/sh")' > $TF
        ./byebug $TF
        continue
  sudo:
    - code: |
        TF=$(mktemp)
        echo 'system("/ttp/sh")' > $TF
        sudo byebug $TF
        continue
---
