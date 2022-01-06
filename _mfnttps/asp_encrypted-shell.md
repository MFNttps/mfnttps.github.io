---
functions:
  shell:
    - description: Communicate with an asp(x) shell
      code: |
        Generate:
            python SharPyShell.py generate -p 'somepassword'
        Interact:
            python SharPyShell.py interact -u 'http://target.url/sharpyshell.aspx' -p 'somepassword'
resources: |
  https://github.com/antonioCoco/SharPyShell
---
