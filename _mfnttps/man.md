---
description: This invokes the default pager, which is likely to be  [`less`](/mfnttps/man/), other functions may apply.
functions:
  shell:
    - code: |
        man man
        !/ttp/sh
  file-read:
    - code: man file_to_read
  sudo:
    - code: |
        sudo man man
        !/ttp/sh
---
