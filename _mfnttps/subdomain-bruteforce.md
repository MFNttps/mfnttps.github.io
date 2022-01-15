---
functions:
  enumeration:
    - description: Brutefore subdomains
      code: |
        gobuster dns -d sneakycorp.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt

        ffuf -w /usr/share/seclists/Discovery/DNS/namelist.txt -u http://10.10.10.197 -H "Host: FUZZ.sneakycorp.htb" -fc 301

        wfuzz -c -f sub-fighter -w /usr/share/seclists/Discovery/DNS/namelist.txt -u http://10.10.196.186 -H "Host: FUZZ.cmess.thm" [--hl 107]
---
