---
functions:
  shell:
    - code: run-parts --new-session --regex '^sh$' /ttp
  sudo:
    - code: sudo run-parts --new-session --regex '^sh$' /ttp
  suid:
    - code: ./run-parts --new-session --regex '^sh$' /ttp --arg='-p'
---
