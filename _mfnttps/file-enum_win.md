---
functions:
  enumeration:
    - description: Perform file searching on Windows
      code: |
        Get-ChildItem -Path C:\Test

        Get-ChildItem -Path C:\Test\*.bat -Recurse -Force

        Get-ChildItem -Path ./* -Include *.txt,*.bat
resources:|
  https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7
---
