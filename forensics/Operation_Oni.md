## Operation Oni

Challenge description:
```
Note: you must launch a challenge instance in order to view your disk image download link.

Description
Download this disk image, find the key and log into the remote machine.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
Additional details will be available after launching your challenge instance.
```
After launching challenge instance:
```
Remote machine: ssh -i key_file -p 55400 ctf-player@saturn.picoctf.net
```

Provided disk image:
```
https://artifacts.picoctf.net/c/71/disk.img.gz
```

The file is analyzed:
```
file disk.img.gz
```
Output:
```
disk.img.gz: gzip compressed data, was "disk.img", last modified: Wed Oct  6 14:32:01 2021, from Unix, original size modulo 2^32 241172480
```

It is decompressed using:
```
gunzip disk.img.gz
```

It is re-analyzed:
```
 file disk.img
```

Output:
```
disk.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,223,19), startsector 2048, 204800 sectors; partition 2 : ID=0x83, start-CHS (0xc,223,20), end-CHS (0x1d,81,52), startsector 206848, 264192 sectors
```

To check the partitions, ```mmls``` is used:
```
mmls disk.img
```

Output:
```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```

Partition 2 is checked:
```
fls -o 0000002048 disk.img
```
Output:
```
d/d 11: lost+found
r/r 12: ldlinux.sys
r/r 13: ldlinux.c32
r/r 15: config-virt
r/r 16: vmlinuz-virt
r/r 17: initramfs-virt
l/l 18: boot
r/r 20: libutil.c32
r/r 19: extlinux.conf
r/r 21: libcom32.c32
r/r 22: mboot.c32
r/r 23: menu.c32
r/r 14: System.map-virt
r/r 24: vesamenu.c32
V/V 25585:      $OrphanFiles
```

Partition 3 is checked:
```
fls -o 0000206848 disk.img
```

Output:
```
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 79: proc
d/d 80: dev
d/d 81: tmp
d/d 82: lib
d/d 85: var
d/d 94: usr
d/d 104:        bin
d/d 118:        sbin
d/d 464:        media
d/d 468:        mnt
d/d 469:        opt
d/d 470:        root
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
```
root is checked:
```
fls -o 0000206848 disk.img 470
```

Output:
```
r/r 2344:       .ash_history
d/d 3916:       .ssh
```

ssh directory is checked:
```
fls -o 0000206848 disk.img 3916
```

Output:
```
r/r 2345:       id_ed25519
r/r 2346:       id_ed25519.pub
```

Each file is checked:
```
icat -o 0000206848 disk.img 2345
```
Output:
```
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
```

The next one:
```
icat -o 0000206848 disk.img 2346
```

Output:
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGCtd7hso2E7OQItY6aTjMMyKZb1FVmeBfnVjyHcGYos root@localhost
```

The file is transferred to the local machine:
```
icat -o 0000206848 disk.img 2345 > id_ed25519
```
On checking file permissions:
```
ls -l id_ed25519
```
Output:
```
-rw-r--r-- 1 advita advita 411 Dec 23 13:10 id_ed25519
```

The permissions are changed:
```
 chmod 600 id_ed25519
```
600 ensures that only the owner has full read and write file access.

Login to ssh:
```
ssh -i id_ed25519 -p 55400 ctf-player@saturn.picoctf.net
```
Output:
```
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$
```
On checking the files using ```ls```, we find:
```
flag.txt
```

On reading the file using ```cat```, the flag is found:
```
picoCTF{k3y_5l3u7h_af277f77}
```
