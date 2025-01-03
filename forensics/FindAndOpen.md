## FindAndOpen

Challenge description:
```
Someone might have hidden the password in the trace file.
Find the key to unlock this file. This tracefile might be good to analyze.
```

Hints:
```
Download the pcap and look for the password or flag.
Don't try to use a password cracking tool, there are easier ways here.
```

File to unlock:
```
https://artifacts.picoctf.net/c/492/flag.zip
```

Tracefile:
```
https://artifacts.picoctf.net/c/492/dump.pcap
```

The tracefile is downloaded and opened using WireShark. On analyzing, Packet 48 is interesting because of the irregular number of bytes of data (remaining packets are 29 or 33 bytes while 48 has 56 bytes).

The data looks like base64 encoded text:
```
VGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=
```

It is decoded in the terminal:
```
echo "VGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=" | base64 -d
```

Output:
```
This is the secret: picoCTF{R34DING_LOKd_
```

This output is used as the password for the flag file that is provided to unlock.
After entering the password and using Vim to view the file, the following output is viewed, which is our flag:
```
picoCTF{R34DING_LOKd_fil56_succ3ss_cbf2ebf6}
``` 
