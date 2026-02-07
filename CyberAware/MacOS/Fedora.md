# TẠO USB Fedora Workstation
1. Download Fedora Workstation: https://www.fedoraproject.org/workstation/download
2. Doanload balenaEtcher: https://etcher.balena.io/#download-etcher
3. diskutil eraseDisk FAT32 FEDORA_USB GPT /dev/disk4
4. diskutil unmountDisk /dev/disk4
5. sudo dd if=Fedora-Workstation-Live-x86_64-*.iso of=/dev/rdisk4 bs=1m status=progress
6. diskutil mountDisk /dev/disk4
