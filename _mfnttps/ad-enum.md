---
functions:
  enumeration:
    - description: Basic Active Directory Enumeration for Kerberos Tickets
      code: |
      	./ad-enum.ps1

                              /^\
                              | |
                              |-|
                         /^\  | |
                  /^\  / [_] \+-+
                 |---||-------| |
        _/^\_    _/^\_|  [_]  |_/^\_   _/^\_
        |___|    |___||_______||___|   |___|
         | |======| |===========| |=====| |
         | |      | |    /^\    | |     | |
         | |      | |   |   |   | |     | |
         |_|______|_|__ |   |___|_|_____|_|

        --------------------------------
          LIST AD Group RELATIONSHIPS
        --------------------------------
        Parent: Denied RODC Password Replication Group  -->  Child: Domain Controllers
        Parent: Denied RODC Password Replication Group  -->  Child: Schema Admins
        Parent: Administrators  -->  Child: Enterprise Admins
        Parent: Denied RODC Password Replication Group  -->  Child: Enterprise Admins
        Parent: Denied RODC Password Replication Group  -->  Child: Cert Publishers
        Parent: Administrators  -->  Child: Domain Admins
        Parent: Denied RODC Password Replication Group  -->  Child: Domain Admins
        Parent: Users  -->  Child: Domain Users
        Parent: Guests  -->  Child: Domain Guests
        Parent: Denied RODC Password Replication Group  -->  Child: Group Policy Creator Owners
        Parent: Denied RODC Password Replication Group  -->  Child: Read-only Domain Controllers
        Parent: Company_Mail  -->  Child: Mail_Editor
        Parent: Mail_Reader  -->  Child: Mail_Editor
        Parent: Company_Mail  -->  Child: Mail_Reader
        ---------------------------
            LIST DOMAIN ADMINS
        ---------------------------
        Usernames:
        	 Albert
        	 David
        	 Administrator
        ---------------------------
          LIST AD SERVICE ACCOUNTS
        ---------------------------


        Hostname   : xor-dc01.xor.com
        SPN        : Dfsr-12F9A27C-BF97-4787-9364-D31B6C55EB04/xor-dc01.xor.com
        Service    : Dfsr-12F9A27C-BF97-4787-9364-D31B6C55EB04
        DomainName : xor-dc01.xor.com
        IPAddress  : 10.11.1.120

        Hostname   : XOR-APP07
        SPN        : TERMSRV/XOR-APP07
        Service    : TERMSRV
        DomainName : XOR-APP07.xor.com
        IPAddress  : 10.11.1.122

        Hostname   : XOR-APP23
        SPN        : TERMSRV/XOR-APP23
        Service    : TERMSRV
        DomainName : XOR-APP23.xor.com
        IPAddress  : 10.11.1.121

        Hostname   : XOR-APP59
        SPN        : TERMSRV/XOR-APP59
        Service    : TERMSRV
        DomainName : xor-app59.xor.com
        IPAddress  : ::1

        Hostname   : ExchangeService.xor.com
        SPN        : HTTP/ExchangeService.xor.com
        Service    : HTTP
        DomainName : ExchangeService.xor.com
        IPAddress  : 10.60.60.227

        Hostname   : ExtMail.xor.com
        SPN        : HTTP/ExtMail.xor.com
        Service    : HTTP
        DomainName : ExtMail.xor.com
        IPAddress  : 10.60.60.227

        Hostname   : changepw
        SPN        : kadmin/changepw
        Service    : kadmin
        DomainName : 
        IPAddress  : 

        Hostname   : xor-app23.xor.com
        SPN        : MSSQLSvc/xor-app23.xor.com:1433
        Service    : MSSQLSvc
        DomainName : xor-app23.xor.com
        IPAddress  : 10.11.1.121



        ------------------------------------------------

resources: |
  https://github.com/unkn0wnsyst3m/scripts/blob/master/ad-enum.ps1

---
