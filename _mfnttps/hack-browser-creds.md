---
functions:
  enumeration:
    - description: Crack Firefox Saved Passwords
      code: |
        Required files, typically in %AppData%\Roaming\Mozilla
          key3.db
          signons.sqlite
          cert8.db
          user password
        python2 ffpassdecrypt.py -P .


resources: |
  https://github.com/pradeep1288/ffpasscracker
---
