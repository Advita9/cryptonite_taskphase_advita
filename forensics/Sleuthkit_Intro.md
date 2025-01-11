## Sleuthkit Intro

Challenge description:
```
Download the disk image and use mmls on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
Download disk image
Access checker program: nc saturn.picoctf.net 52319
```

Link provided:
```
https://artifacts.picoctf.net/c/164/disk.img.gz
```

According to challenge instructions, we cd into the /tmp directory and download the file provided:
```
cd /tmp

wget https://artifacts.picoctf.net/c/164/disk.img.gz
```

It is unzipped:
```
gunzip disk.img.gz
```

The file partitions are checked:
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
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```

The challenge instance is initiated:
```
nc saturn.picoctf.net 52319
```

Output:
```
What is the size of the Linux partition in the given disk image?
Length in sectors:
```

The length is entered:
```
202752
```

We get flag as output:
```
Great work!
picoCTF{mm15_f7w!}
```
