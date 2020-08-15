---
functions:
  privilege-escalation:
    - description: Bypass powershell script execution policies
      code: |
        powershell -c set-executionpolicy -scope CurrentUser bypass <script> 
---
