---
functions:
  pivoting:
    - description: Chisel Single Port Fowarding
      code: |
        Client
        chisel.exe client <server> R:<port-to-forward>:<server-listening-ip-port>
        chisel.exe client 10.10.14.10:8000 R:445:127.0.0.1:445

        Server
        chisel server -p 8000 --reverse
    - description: Chisel Socks5 Proxy
      code: |
        Client
        chisel.exe client 10.10.14.3:8000 R:socks

        Server
        chisel server -p 8000 --socks5 --reverse
resources: |
  https://github.com/jpillora/chisel
  https://medium.com/geekculture/chisel-network-tunneling-on-steroids-a28e6273c683
---
