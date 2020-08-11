---
functions:
  Pivoting:
    - description: Local SSH port fowarding
      code: |
        Login to 192.168.119.149 with username 'kali' and instruct x.44 to forward all 
        requests to 0.0.0.0:445 and redirect to 172.16.149.5:445
          ssh -f -N -L [bind_address:]port:host:hostport [username@address]
          ssh -f -N -L 0.0.0.0:445:172.16.149.5:445 kali@192.168.119.149
    - description: Remote SSH port fowarding
      code: |
        From the P.O.V of a current access: [you do this]:[I'll do this]
          ssh -f -N -R [bind_address:]port:host:hostport [username@address]
        Login to 192.168.119.149 with username 'kali' and instruct x.149 to listen on 
        0.0.0.0:2221 (you) and bridge that port to access 127.0.0.1:3306 (me)
          ssh -f -N -R 0.0.0.0:2221:127.0.0.1:3306 kali@192.168.119.149
    - description: Dynamic-Local SSH port fowarding
      code: |
        Setup a local socks proxy to forward all traffic to the system you connect
         to (via the new ssh tunnel)

        Create socks proxy on port 8080 and push traffic to 192.168.119.149:
        ssh -N -f -D 127.0.0.1:8080 kali@192.168.119.149
    - description: Dynamic-Remote SSH port fowarding
      code: |
        Setup a remote socks proxy to forward all traffic to the current system 
         to (via the new ssh tunnel)

        Create socks proxy on port 1080 on remote system 192.168.119.149:
        ssh -N -f -R 127.0.0.1:1080 kali@192.168.119.149
    - description: Dynamic-Remote SSH port fowarding (older ssh clients)
      code: |
        Setup a remote socks proxy to forward all traffic to the current system 
         to (via the new ssh tunnel)

        (1) Create remote port forwarding on port 2222 on remote system 192.168.119.149
        and forward to port 8888 of the local system
        (2) Traffic will reach local port 8888 and hit the socks proxy:
        ssh -f -N -R 0.0.0.0:2222:127.0.0.1:8888 kali@192.168.119.149
        ssh -N -D 8888 127.0.0.1
    - description: Create key-pairs to avoid password prompts
      code: |
        1. ssh-keygen ([enter] through all prompts)
        2. copy public key
        3. only allow port forwarding (no key hijack):
        - add to ~/.ssh/authorized_keys
        from="10.11.1.250",command="echo 'This account can only be used for port forwarding'",no-agent-forwarding,no-X11-forwarding,no-pty ssh-rsa <pub key>
        4. add private key to system and append "-i <key>" to all ssh commands

---
