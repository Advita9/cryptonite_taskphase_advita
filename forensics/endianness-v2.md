## endianness-v2

Challenge description:
```
Here's a file that was recovered from a 32-bits system that organized the bytes a weird way. We're not even sure what type of file it is.
Download it here and see what you can get out of it
```

Based on the description, it points to some sort of byte manipulation.

Provided file:
```
https://artifacts.picoctf.net/c_titan/114/challengefile
```

On looking through the file with ```file``` command following output is displayed, which does not reveal anthing:
```
challengefile: data
```

Next ```exiftool``` is installed:
```
sudo apt install libimage-exiftool-perl
```

The file is analyzed:
```
exiftool challengefile
```

The output:
```
ExifTool Version Number         : 12.40
File Name                       : challengefile
Directory                       : .
File Size                       : 3.3 KiB
File Modification Date/Time     : 2024:03:12 06:06:50+05:30
File Access Date/Time           : 2024:12:11 15:14:59+05:30
File Inode Change Date/Time     : 2024:12:11 15:14:44+05:30
File Permissions                : -rw-r--r--
Warning                         : Processing JPEG-like data after unknown 1-byte header
```

This implies that it is a JPEG file but with a wrong header.

Ghex is installed :
```
sudo apt install ghex
```

It is used to lookup the hex header signature of the file:
```
ghex challengefile
```

The first line of the header is:
```
E0 FF D8 FF
```
Based on research, typical JPEG files have a header signature:
```
FF D8 FF E0
```

This implies, that in this file the first 4 bytes have been reversed.


A script is written to:
1. Read the file in binary
2. Split the contents into chunks, each chunk with 4 bytes
3. Reverse the order of each 4 byte chunk
4. Write the corrected bytes back into a new file

The code is as follows:
```
def reverse_bytes_in_file(input_file, output_file):
    with open(input_file, "rb") as f:
        data = f.read()
    
    chunks = [data[i:i+4] for i in range(0, len(data), 4)]
    
    reversed_chunks = [chunk[::-1] for chunk in chunks]
    
    corrected_data = b"".join(reversed_chunks)
    
    with open(output_file, "wb") as f:
        f.write(corrected_data)

input_file = "challengefile"
output_file = "corrected_file.jpg"

reverse_bytes_in_file(input_file, output_file)

```

This script is run and the ```corrected_file.jpg``` file is created.
On opening the image the flag is found :
```
picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_94cc03f3}
```
