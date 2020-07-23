---
functions:
  shell:
    - code: |
        ed
        !/ttp/sh
  file-write:
    - code: |
        ed file_to_write
        a
        DATA
        .
        w
        q
  file-read:
    - code: |
        ed file_to_read
        ,p
        q
  sudo:
    - code: |
        sudo ed
        !/ttp/sh
  limited-suid:
    - code: |
        ./ed
        !/ttp/sh
---
