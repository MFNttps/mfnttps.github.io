---
functions:
  enumeration:
    - description: Get running processes, handles, and command line parameters
      code: |
        gwmi win32_process | select name, Handle, CommandLine | format-table -autosize
        
        get-process | select ID,Name,Path | format-table -autosize

---
