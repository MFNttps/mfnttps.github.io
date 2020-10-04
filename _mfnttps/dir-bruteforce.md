---
functions:
  enumeration:
    - description: Brutefore a website's directory structure
                   and output results
      code: |
        gobuster dir -u http://10.10.10.194:8080 -w /usr/share/wordlists/dirb/common.txt -x txt,php -t 5


---
