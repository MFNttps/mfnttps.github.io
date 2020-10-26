---
functions:
  enumeration:
    - description: Brutefore subdomains
      code: |
        gobuster dns -d sneakycorp.htb -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt

---
