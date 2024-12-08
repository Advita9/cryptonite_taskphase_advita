## Trivial Flag Transfer Protocol

The challenge description is as follows:
```
Figure out how they moved the flag.
```
The hint provided is:
```
What are some other ways to hide data?
```
The link to the file is:
```
https://mercury.picoctf.net/static/fb24ddcfaf1e297be525ba7474964fa5/tftp.pcapng
```

the file properties are understood using:
```
file tftp.pcapng
```

The output is:
```
tftp.pcapng: pcapng capture file - version 1.0
```
Thus it is a tftp file. Wireshark is downloaded using:
```
sudo apt install wireshark-qt
```
The downloaded file is accessed with WireShark:
```
wireshark tftp.pcapng
```

The wireshark window opens and the following filter is applied to display only tftp type files:
```
tftp.type
```

The files displayed are all saved into our workspace into the wireshark_forensics_files directory.

The files downloaded:
```
instructions.txt       picture1.bmp       picture2.bmp       picture3.bmp      'plan'   program.deb
```
The instructions.txt file is read:
```
cat instructions.txt
```
The output is:
```
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
```
This is put into a rot14 decoder and the output is:
```
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```
After applying spaces, it can be understandable:
```
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN
```
This hints towards the ```plan``` file, so we read it. The output is:
```
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF
```

It is put into a ROS13 decoder again and the output is:
```
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```

After adding spaces, it makes sense:
```
I USED THE PROGRAM AND HID IT WITH- DUEDILIGENCE. CHECK OUT THE PHOTOS
```

This hints to the ```program.deb``` file.

The program is installed using:
```
sudo apt-get install ./program.deb
```
The console output suring installation is:
```
[sudo] password for advita:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'steghide' instead of './program.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 steghide : Depends: libjpeg62-turbo (>= 1:1.3.1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Thus the true name of the program is steghide. On researching online, steghide supports hiding data in bmp file. So the flag needs to be extracted from one of the image files, as also stated in the hint.

steghide is then downloaded using:
```
sudo apt install steghide
```

Each individual image file is checked:
```
steghide extract -sf picture1.bmp -p DUEDILIGENCE
steghide extract -sf picture2.bmp -p DUEDILIGENCE
steghide extract -sf picture3.bmp -p DUEDILIGENCE
```
 Finally the third one gives this output:
```
wrote extracted data to "flag.txt".
```
The file is read:
```
cat flag.txt
```
 The output reveals the flag:
```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```




