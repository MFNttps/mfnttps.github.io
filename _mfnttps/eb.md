---
description: This invokes the default logging service, which is likely to be [`journalctl`](/mfnttps/journalctl/), other functions may apply. For this to work the target must be connected to AWS instance via EB-CLI.
functions:
  shell:
    - code: |
        eb logs
        !/ttp/sh
  sudo:
    - code: |
        sudo eb logs
        !/ttp/sh
---
