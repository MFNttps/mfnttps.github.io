---
functions:
  enumeration:
    - description: Brutefore a website's directory structure
                   and output results
      code: |
        gobuster dir -u http://10.10.10.194:8080 -w /usr/share/wordlists/dirb/common.txt -x txt,php -t 5

        gobuster dir -u http://doctors.htb -w /usr/share/wordlists/dirb/big.txt -x txt,sh,php,html -q -t 10 -c "session=eyJfZnJlc2giOmZhbHNlfQ.X8vtQA.BYnd7TX1mCjNoHGLClgG8o7CN-A"

        proxy support: gobuster dir --proxy socks5://127.0.0.1:1080 -w /usr/share/dirb/wordlists/big.txt --url http://10.1.1.65 -x asp,aspx,php,txt,sh -t 40

        feroxbuster -u http://192.168.113.123/ -x jsp,php,pl,txt,sh -w /usr/share/wordlists/dirb/big.txt

        cat /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt /usr/share/wordlists/dirb/big.txt '/usr/share/wordlists/dirbuster/*' /usr/share/wordlists/wfuzz/webservices/ws-dirs.txt | sort -u > megadir.txt
---
