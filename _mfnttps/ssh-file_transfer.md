---
functions:
  file-transfer:
    - description: Transfer files through an ssh socket with scp
      code: |
        Create your ssh connetion with a master socket
          proxychains -f proxychains.conf ssh root@10.0.20.1 -oStrictHostKeyChecking=no -oUserKnownHostsFile=/dev/null -MS /tmp/ssh -vv -i priv.key

        Upload -
          scp -vvv -o "ControlPath=/tmp/ssh" source @:destination
          scp -vvv -o "ControlPath=/tmp/ssh" linpeas.sh @:/tmp/1.sh

        Download -
          scp -vvv -o "ControlPath=/tmp/ssh" @:source destination
          scp -vvv -o "ControlPath=/tmp/ssh" @:/tmp/1.sh linpeas.sh

resources: |

---
