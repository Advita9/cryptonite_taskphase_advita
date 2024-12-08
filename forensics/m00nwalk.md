## m00nwalk

The challenge description is as follows:
```
Decode this message from the moon.
```

The hints given are:
```
How did pictures from the moon landing get sent back to Earth?

What is the CMU mascot?, that might help select a RX option
```
The wav file provided is :
```
https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav
```
Researching on the hints, SSTV which is Slow-scan television was used for sending pictures from the moon landing on earth.

On further research online, I found that ```qsstv``` is used to convert/decode SSTV audio files to images. I looked up rsources for how to do this on Ubuntu.

The following dependencies were installed:
```
sudo apt-get install qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools

sudo apt-get install qsstv

sudo apt install pulseaudio-utils

sudo apt install pavucontrol
```

A null audio sink module is loaded to act as a virtual cable:
```
pactl load-module module-null-sink sink_name=virtual-cable
```
An id of 22 is received as output.

PulseAudio Volume Control is started:
```
pavucontrol
```

QSSTV is launched
```
qsstv
```

The CMU mascot for the second question is "Scotty". Based on this hint, the mode selected in QSSTV is ```Scottie 1```.

The audio file is played:
```
paplay -d virtual-cable message.wav
```
On the QSSTV window, an image is displayed which displays the flag.

```
picoCTF{beep_boop_im_in_space}
```

