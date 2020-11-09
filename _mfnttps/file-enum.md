---
functions:
  enumeration:
    - description: Perform file searching on Windows
      code: |
        WINDOWS
        Get-ChildItem -Path C:\Test

        Get-ChildItem -Path C:\Test\*.bat -Recurse -Force

        Get-ChildItem -Path ./* -Include *.txt,*.bat -Recurse

        Get-ChildItem -Path ./Data* -Include *.* -Recurse |  Where-Object {$_.LastWriteTime -gt (get-date -month 7 -day 4)}

        Get-ChildItem -Path ./Data* -Recurse |  Where-Object {$_.LastWriteTime -gt (get-date -month 7 -day 4) -and $_.Attributes -notcontains "Directory"}

        NIX
        find $directory -type f -name "*.sh" 2>/dev/null
resources:
  https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7
  
  https://www.pdq.com/blog/using-get-childitem-find-files/
---