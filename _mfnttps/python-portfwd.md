---
functions:
  pivoting:
    - description: Python port fowarding
      code: |
        Listen on port 9999 and forward the connection to localhost port 8080
        python3 tcpforward.py -l 10.10.10.218:9999 -c 127.0.0.1:8080
resources: |
  https://gist.github.com/MidnightSeer/72df188aa2fa6a18a963c0310d895529#file-tcpforward-py
---
