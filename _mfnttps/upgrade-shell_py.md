---
functions:
  shell:
    - description: Upgrade to a psuedo interactive shell using python
      code: |
        LINUX:
        python -c 'import pty; pty.spawn("/bin/bash")'
        python -c 'import pty; pty.spawn("/bin/sh")'
        python3 -c 'import pty; pty.spawn("/bin/bash")'
        python3 -c 'import pty; pty.spawn("/bin/sh")'

        CTRL-Z -- background job
        stty -a  → get cols and rows values   (a)
        stty raw -echo      <--- push raw commands through the shell
        fg     -- return job to foreground
        {enter} x2     - if needed
        
        In shell:
        stty rows 29 columns 235    - values taken from (a) above

        fix PATH:
        PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"


        "reset" when you exit the shell


        NEW:

        stty -icanon -echo
        python -c 'import pty; pty.spawn("/bin/bash")'
  resources: |
    https://stackoverflow.com/questions/29317933/vi-over-netcat-session
---
