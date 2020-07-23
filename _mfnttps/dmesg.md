---
functions:
  file-read:
    - description: This is not suitable for ttpary files.
      code: |
        LFILE=file_to_read
        dmesg -rF "$LFILE"
  shell:
    - description: This invokes the default pager, which is likely to be [`less`](/mfnttps/less/), other functions may apply.
      code: |
        dmesg -H
        !/ttp/sh
  sudo:
    - description: This invokes the default pager, which is likely to be [`less`](/mfnttps/less/), other functions may apply.
      code: |
        sudo dmesg -H
        !/ttp/sh
---
