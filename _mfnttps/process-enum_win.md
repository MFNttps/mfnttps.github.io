---
functions:
  enumeration:
    - description: Get running processes, handles, and command line parameters
      code: |
        gwmi win32_process | select name, Handle, CommandLine | format-table -autosize
        get-process | select ID,Name,Path | format-table -autosize


        
        filter Get-ProcessOwner
		{
		  $id = $_.ID
		  $info = (Get-WmiObject -Class Win32_Process -Filter "Handle=$id").GetOwner()
		  if ($info.ReturnValue -eq 2)
		  {
		    $owner = '[Access Denied]'
		  }
		  else
		  {
		    $owner = '{0}\{1}' -f $info.Domain, $info.User
		  }
		  $_ | Add-Member -MemberType NoteProperty -Name Owner -Value $owner -PassThru
		}
        Get-Process | Get-ProcessOwner | Select-Object -Property Name, ID, Owner, Path | sort-object ID
---
