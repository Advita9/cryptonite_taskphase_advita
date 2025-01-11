## PcapPoisoning

Challenge description:

How about some hide and seek heh?
Download this file and find the flag.

File link:
```
https://artifacts.picoctf.net/c/371/trace.pcap
```

The first approach was to examine the file using Wireshark to analyze network traffic. However, since the number of packets is huge, the file was examined using the command line. After downloading the file, the following command was used to extract the flag:
```
 strings trace.pcap | grep picoCTF{
```

This extracts all the strings and filters the ones starting with ```picoCTF{```.

Output:
```
picoCTF{P64P_4N4L7S1S_SU55355FUL_fc4e803f}
```
