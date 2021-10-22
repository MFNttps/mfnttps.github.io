---
functions:
  pivoting:
    - description: Python port fowarding
      code: |
        Listen on port 9999 and forward the connection to localhost port 8080
        python3 tcpforward.py -l 10.10.10.218:9999 -c 127.0.0.1:8080

        Listen on port 8080 and forward the connection to 192.168.119.214 port 8080
        python tcpforward.py 10.2.2.218:8080 192.168.119.214:8080

resources: |
  https://gist.github.com/MidnightSeer/72df188aa2fa6a18a963c0310d895529#file-tcpforward-py
  https://gist.github.com/MidnightSeer/37d5d4c23bedaf9ca02c99c7b78ad094#file-tcpforwardpy2-py
---
