---
description: |
  This invokes the default pager, which is likely to be [`less`](/mfnttps/less/), other functions may apply.

  This might not work if run by unprivileged users depending on the system configuration.
functions:
  shell:
    - code: |
        journalctl
        !/ttp/sh
  sudo:
    - code: |
        sudo journalctl
        !/ttp/sh
---
