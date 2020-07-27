---
functions:
  lateral-movement:
    - description: Log into an ssh server and give it instructions to redirect traffic.
      code: |
        Local:
        ssh -f -N -L [bind_address:]port:host:hostport [username@address]
        ssh -f -N -L 0.0.0.0:445:172.16.149.5:445 student@192.168.149.44
        
        Remote:
        - From the P.O.V of current access; [you do this]:[I'll do this]
        ssh -f -N -R [bind_address:]port:host:hostport [username@address]
        - Login to 192.168.119.149 with username 'kali'
        - Instruct x.149 to listen on 0.0.0.0:2221 (you) and bridge that port to access 127.0.0.1:3306 (me)
        ssh -f -N -R 0.0.0.0:2221:127.0.0.1:3306 kali@192.168.119.149
---
