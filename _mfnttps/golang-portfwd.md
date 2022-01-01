---
functions:
  pivoting:
    - description: Golang port fowarding
      code: |
        Listen on port 9999 and forward the connection to localhost port 8080
        
        usage: TCP Forwarding [-h|--help] [-l|--listen "<value>"] [-c|--connect "<value>"]

                      Simple TCP Forwarder
        Arguments:

          -h  --help     Print help information
          -l  --listen   IP Address and Port. Default: 0.0.0.0:9999
          -c  --connect  IP Address and Port. Default: 127.0.0.1:9999

        .\port-forward.exe -l 0.0.0.0:9999 -c 127.0.0.1:8080
        [*] L:0.0.0.0:5555 --> C:10.0.0.237:80
        2021/12/31 21:44:20 10.0.0.109:54623 <--> {Proxy} <--> 10.0.0.237:80
        2021/12/31 21:44:29 10.0.0.109:54625 <--> {Proxy} <--> 10.0.0.237:80
        
        Of course you can change the default options too so omit the need for arguments

resources: |
  https://gist.github.com/unkn0wnsyst3m/26a5e1744939df6d208aecb9a3eb6667
---
