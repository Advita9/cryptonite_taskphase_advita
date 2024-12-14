## MSB

Challenge description:
```
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image...
Download the image here
```

Hints:
```
What's causing the 'corruption' of the image?

```

Image source link:
```
https://artifacts.picoctf.net/c/303/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
```

Based on the challenge title, it can be deduced that the Most Significant Bit of the image needs to be extracted.

A premade python file for conversion to msb and lsb is found:
```
https://raw.githubusercontent.com/Pulho/sigBits/refs/heads/master/sigBits.py
```

Based on the arguments of the README of the repo, the following command is written for file generation:
```
python3 sigBits.py -t=msb Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
```

Output:
```
Done, check the output file!
```

Existing files in the directory are checked, ``` outputSB.txt``` is the file that has been created.

The file is opened in vim:
```
vim outputSB.txt
```

To search within the contents, ```/pico``` is used and the flag is located:
```
picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_24d55bee}
```

