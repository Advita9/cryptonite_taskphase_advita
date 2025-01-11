## HideToSee

Challenge description:
```
How about some hide and seek heh?
Look at this image here.
```

Hints:
```
Download the image and try to extract it.
```

Image link:
```
https://artifacts.picoctf.net/c/238/atbash.jpg
```

Steganograph is the art of hiding data within a non-secret medium. 
To extract data from an image using ```steghide```, the following command is used:
```
steghide --extract -sf atbash.jpg
```

This prompts us to write a passphrase. The Enter key is pressed without entering anything. Output:
```
Enter passphrase:
wrote extracted data to "encrypted.txt".
```

The file read using ```cat```:
Output:
```
krxlXGU{zgyzhs_xizxp_8z0uvwwx}
```
Based on the file name, it means the Atbash cipher, which mainl reverses the letters.

An online decoder is used to decode it and the output is the flag:
```
picoCTF{atbash_crack_8a0feddc}
```

