---
functions:
  persistence:

    - description: Use system startup registry to run a program
      code: |
        reg query HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run

        reg add "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run" /v "VMware Health" /d "C:\ProgramData\VMwareHealthMonitor.exe"


resources: |
  https://www.cyborgsecurity.com/cyborg-labs/hunting-for-persistence-registry-run-keys-startup-folder/

---