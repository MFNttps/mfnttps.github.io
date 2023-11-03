---
functions:
  ttp-tip:
    - description: Start a detached process
      code: |
        powershell -c "start-process shell.exe -RedirectStandardOutput '.\console.out' -RedirectStandardError '.\console.err'"
resources: |
  https://stackoverflow.com/questions/25023458/start-a-detached-background-process-in-powershell
---