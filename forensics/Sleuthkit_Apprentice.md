## Sleuthkit Apprentice

Challenge description:
```
Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
Download compressed disk image
```
Link provided:
```
https://artifacts.picoctf.net/c/137/disk.flag.img.gz
```
We enter the /tmp using cd as specified in the description and download the file:
```
cd /tmp

wget https://artifacts.picoctf.net/c/137/disk.flag.img.gz
```

We unzip the file:
```
gunzip disk.flag.img.gz
```

We check the file type:
```
file disk.flag.img
```

Output:
```
disk.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,223,19), startsector 2048, 204800 sectors; partition 2 : ID=0x82, start-CHS (0xc,223,20), end-CHS (0x16,111,25), startsector 206848, 153600 sectors; partition 3 : ID=0x83, start-CHS (0x16,111,26), end-CHS (0x26,62,24), startsector 360448, 253952 sectors
```

We check the partition table:
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
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
```

We check the individual file partitions until we find root in:
```
fls -o 0000360448 disk.flag.img
```

Output:
```
d/d 451:        home
d/d 11: lost+found
d/d 12: boot
d/d 1985:       etc
d/d 1986:       proc
d/d 1987:       dev
d/d 1988:       tmp
d/d 1989:       lib
d/d 1990:       var
d/d 3969:       usr
d/d 3970:       bin
d/d 1991:       sbin
d/d 1992:       media
d/d 1993:       mnt
d/d 1994:       opt
d/d 1995:       root
d/d 1996:       run
d/d 1997:       srv
d/d 1998:       sys
d/d 2358:       swap
V/V 31745:      $OrphanFiles
```

We look into root:
```
fls -o 0000360448 disk.flag.img 1995
```

Output:
```
r/r 2363:       .ash_history
d/d 3981:       my_folder
```

We look into my_folder:
```
fls -o 0000360448 disk.flag.img 3981
```

Output:
```
r/r * 2082(realloc):    flag.txt
r/r 2371:       flag.uni.txt
```

As flag.txt has an asterix, it means it is deleted. Thus we look into flag.uni.txt:
```
icat -o 0000360448 disk.flag.img 2371
```

The flag is found:
```
picoCTF{by73_5urf3r_adac6cb4}
```
