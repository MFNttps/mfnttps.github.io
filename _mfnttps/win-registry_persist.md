---
functions:
  persistence:

    - description: Use system startup registry to run a program when a user logs in (then remove the registry key)
      code: |
        HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
        HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
        HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
        HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce

        reg query <key>
        reg add <key> /v "VMware Health" /d "C:\ProgramData\VMwareHealthMonitor.exe"

    - description: Use system startup registry to run a service when a user logs in (then remove the registry key)
      code: |
        HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
        HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
        HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServices
        HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServices

        reg query <key>
        reg add <key> /v "VMware Health" /d "C:\ProgramData\VMwareHealthMonitor.exe"

    - description: Use system startup registry to run a program when a user session is created
      code: |
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Shell
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Notify

        reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon" /v Userinit /d "Userinit.exe, C:\ProgramData\VMwareHealthMonitor.exe" /f
        reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon" /v Shell /d "explorer.exe, C:\ProgramData\VMwareHealthMonitor.exe" /f

resources: |
  https://www.cyborgsecurity.com/cyborg-labs/hunting-for-persistence-registry-run-keys-startup-folder/
  https://attack.mitre.org/techniques/T1547/001/
  https://pentestlab.blog/2020/01/14/persistence-winlogon-helper-dll/

---