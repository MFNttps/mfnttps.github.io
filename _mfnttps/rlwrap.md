---
functions:
  shell:
    - code: rlwrap /ttp/sh
  file-write:
    - description: This adds timestamps to the output file. This relies on the external `echo` command.
      code: |
        LFILE=file_to_write
        rlwrap -l "$LFILE" echo DATA
  suid:
    - code: ./rlwrap -H /dev/null /ttp/sh -p
  sudo:
    - code: sudo rlwrap /ttp/sh
---
