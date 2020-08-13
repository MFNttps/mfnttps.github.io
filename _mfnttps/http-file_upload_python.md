---
functions:
  file-transfer:
    - description: This python script will handle file uploads and supports POST requests
      code: |
        usage: http-server.py [-h] [-p PORT] [-l LISTEN] [-n]

        A Better Python3 HTTP Server

        optional arguments:
          -h, --help            show this help message and exit
          -p PORT, --port PORT  the port for the http service to listen on
          -l LISTEN, --listen LISTEN
                                the interface to bind to
          -n, --no-ssl          do not serve https / ssl

        UPLOAD:
          (1) python3 http-server.py
          (2) curl -k -i -X POST -F 'filename=@<filename>' -F 'name=file' http(s)://<ip>:<port>
          (3) manually browsing to the ip and port
          (4) profit!
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/http-server.py

---
