---
functions:
  pivoting:
    - description: View Windows port forwarding rules
      code: |
        netsh interface portproxy show v4tov4
    - description: View Windows firewall rules
      code: |
        netsh advfirewall firewall show rule <rulename>
        netsh advfirewall firewall show rule all direction=out
    - description: Windows rule to forward traffic 
      code: |
        netsh interface portproxy add v4tov4 listenport=5555 listenaddress=192.168.149.10 connectport=80 connectaddress=192.168.119.149
    - description: Delete a Windows port forwarding rule
      code: |
        netsh interface portproxy delete v4tov4 listenport=80 listenaddress=172.16.149.10 protocol=tcp
    - description: Add a Windows firewall rule
      code: |
        netsh advfirewall firewall add rule name="forward_port_rule" protocol=TCP dir=in localip=10.11.0.22 localport=4455 action=allow
        netsh advfirewall firewall add rule name="forward_port_rule" protocol=TCP dir=out localport=53 action=allow
        NOTE: you can remove the "localip" argument to whitelist all IPs
    - description: Delete a Windows port forwarding rule
      code: |
        netsh advfirewall firewall delete rule name="your rule name" dir=in
---
