---
functions:
  pivoting:
    - description: Local SSH port fowarding
      code: |
        Listen on port 9999 and forward the connection to localhost port 8080
        perl tcpforward.pl -l 10.10.10.218:9999 -c 127.0.0.1:8080
resources: |
  https://gist.github.com/MidnightSeer/2f8f986a9687c4fda5ff2d6e902185d2
---
