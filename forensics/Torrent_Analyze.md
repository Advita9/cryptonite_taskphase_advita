## Torrent Analyze

Challenge Description:
```
SOS, someone is torrenting on our network.
One of your colleagues has been using torrent to download some files on the company’s network. Can you identify the file(s) that were downloaded? The file name will be the flag, like picoCTF{filename}. Captured traffic.
```

Hints:
```
Download and open the file with a packet analyzer like Wireshark.

You may want to enable BitTorrent protocol (BT-DHT, etc.) on Wireshark. Analyze -> Enabled Protocols

Try to understand peers, leechers and seeds. Article

The file name ends with .iso
```

Captured traffic file:
```
https://artifacts.picoctf.net/c/165/torrent.pcap
```

The file is opened in WireShark and based on the hints, the ```bt-dht``` filter is applied.

The most common local IP address found is ```192.168.73.132```, so that is added on to the filter:
```
bt-dht and ip.src_host == "192.168.73.132"
```
As we need to find the file downloaded through bit torrent, we need to utilize the info hash.

info hash is a 20 byte SHA-1 hash binary encoded.

All the protocols are traversed until one with info hash is found. In this case the first packet with that was packet 51080. 

The value is:
```
e2467cbf021192c241367b892230dc1e05c0580e
```

A google search is made and a .iso file is found on Linuxtracker (in line with hints).

Thus the flag is:
```
picoCTF{ubuntu-19.10-desktop-amd64.iso}
```

