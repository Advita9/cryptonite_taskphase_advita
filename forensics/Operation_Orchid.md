## Operation Orchid

Challenge description:
```
Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
Download compressed disk image
```

Provided link:
```
https://artifacts.picoctf.net/c/212/disk.flag.img.gz
```
Based on the description, we cd into the /tmp directory to download the file into:
```
cd /tmp
wget https://artifacts.picoctf.net/c/212/disk.flag.img.gz
```

The file type is checked:
```
file disk.flag.img.gz
```

Output:
```
disk.flag.img.gz: gzip compressed data, was "disk.flag.img", last modified: Thu Mar 16 01:56:49 2023, from Unix, original size modulo 2^32 419430400
```
It is extracted:
```
gunzip disk.flag.img.gz
```
The partitions are checked:
```
mmls disk.flag.img
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
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```

The partitions are checked:
```
fls -o 2048
```
Output:
```
Missing image name
usage: fls [-adDFlhpruvV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-m dir/] [-o imgoffset] [-z ZONE] [-s seconds] image [images] [inode]
        If [inode] is not given, the root directory is used
        -a: Display "." and ".." entries
        -d: Display deleted entries only
        -D: Display only directories
        -F: Display only files
        -l: Display long version (like ls -l)
        -i imgtype: Format of image file (use '-i list' for supported types)
        -b dev_sector_size: The size (in bytes) of the device sectors
        -f fstype: File system type (use '-f list' for supported types)
        -m: Display output in mactime input format with
              dir/ as the actual mount point of the image
        -h: Include MD5 checksum hash in mactime output
        -o imgoffset: Offset into image file (in sectors)
        -P pooltype: Pool container type (use '-P list' for supported types)
        -B pool_volume_block: Starting block (for pool volumes only)
        -S snap_id: Snapshot ID (for APFS only)
        -p: Display full path for each file
        -r: Recurse on directory entries
        -u: Display undeleted entries only
        -v: verbose output to stderr
        -V: Print version
        -z: Time zone of original machine (i.e. EST5EDT or GMT) (only useful with -l)
        -s seconds: Time skew of original machine (in seconds) (only useful with -l & -m)
        -k password: Decryption password for encrypted volumes

```

Next, the root is found in partition 411648:
```
fls -o 411648 disk.flag.img
```

Output:
```
d/d 460:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 81: proc
d/d 82: dev
d/d 83: tmp
d/d 84: lib
d/d 87: var
d/d 96: usr
d/d 106:        bin
d/d 120:        sbin
d/d 466:        media
d/d 470:        mnt
d/d 471:        opt
d/d 472:        root
d/d 473:        run
d/d 475:        srv
d/d 476:        sys
d/d 2041:       swap
V/V 51001:      $OrphanFiles
```

We check root further:
```
fls -o 411648 disk.flag.img 472
```
Output:
```
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
```
There is an asterix with ```flag.txt``` which means it is deleted. Thus we look into the encrypted file:
```
icat -o 411648 disk.flag.img 1782
```
Output:
```
Salted__0!-6V0Ul&:pj_1
```

All the offsets of the strings in the file:
```
strings -t d disk.flag.img | grep flag.txt
```
Output:
```
18985524 flag.txt
218985540 flag.txt.enc
219964416 touch flag.txt
219964431 nano flag.txt
219964483 nano flag.txt
219964506 openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
219964588 shred -u flag.txt
303193140 flag.txt
303317044 flag.txt
303317060 flag.txt.enc
303328308 flag.txt
303328324 flag.txt.enc
```
An openssl aes256 encryption with key ```unbreakablepassword1234567``` is used.

The contents are sent to flah.txt.enc:
```
icat -o 411648 disk.flag.img 1782 > flah.txt.enc
```

Now we decrypt:
```
openssl aes256 -d -salt -in flah.txt.enc -out flag.txt -k unbreakablepassword1234567
```

Output:
```
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
800B6F84CF7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:124:
```

The contents of flag.txt are read using ```cat```:
```
picoCTF{h4un71ng_p457_0a710765}
```

Hence the flag is found.
