---
functions:
  file-transfer:
    - description: This python script will handle file downloads to transfer files between systems
      code: |
        usage: http-server.py [-h] [-p PORT] [-l LISTEN] [-n]

        A Better Python3 HTTP Server

        optional arguments:
          -h, --help            show this help message and exit
          -p PORT, --port PORT  the port for the http service to listen on
          -l LISTEN, --listen LISTEN
                                the interface to bind to
          -n, --no-ssl          do not serve https / ssl

        Download Files:
          (1) python3 http-server.py
          (2) manually browsing to http(s)//<ip>:<port>
          (3) browse the directory and/or download files
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/http-server.py

---
