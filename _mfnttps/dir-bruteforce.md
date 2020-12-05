---
functions:
  enumeration:
    - description: Brutefore a website's directory structure
                   and output results
      code: |
        gobuster dir -u http://10.10.10.194:8080 -w /usr/share/wordlists/dirb/common.txt -x txt,php -t 5

        gobuster dir -u http://doctors.htb -w /usr/share/wordlists/dirb/big.txt -x txt,sh,php,html -q -t 10 -c "session=eyJfZnJlc2giOmZhbHNlfQ.X8vtQA.BYnd7TX1mCjNoHGLClgG8o7CN-A"

---
