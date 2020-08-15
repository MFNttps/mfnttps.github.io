---
functions:
  privilege-escalation:
    - description: Get powershell command history
      code: |
        Get Location: (Get-PSReadlineOption).HistorySavePath
        Output Contents: type (Get-PSReadlineOption).HistorySavePath
---
