---
functions:
  shell:
    - code: |
        pg /etc/profile
        !/ttp/sh
  file-read:
    - code: pg file_to_read
  sudo:
    - code: |
        sudo pg /etc/profile
        !/ttp/sh
  suid:
    - code: ./pg file_to_read
---
