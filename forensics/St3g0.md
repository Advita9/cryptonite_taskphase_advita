## St3g0

Challenge description:
```
Download this image and find the flag.
Download image
```
Hints:
```
We know the end sequence of the message will be $t3g0.
```

Provided file:
```
https://artifacts.picoctf.net/c/216/pico.flag.png
```

The file is analyzed:
```
file pico.flag.png
```

Output:
```
pico.flag.png: PNG image data, 585 x 172, 8-bit/color RGBA, non-interlaced
```

To further understand the file, ```binwalk``` is used:
```
binwalk pico.flag.png
```

Output:
```

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 585 x 172, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, default compression
```

This does not reveal anything interesting.

```steganography``` is an additional step used in conjunction with encryption to conceal data.
```zsteg``` is a tool used to detect the LSB steganography of image files.

It is downloaded:
```
sudo apt install ruby
sudo gem install zsteg
```

It is used to analyze the file:
```
zsteg -a pico.flag.png
```
```-a``` tries all known methods.

Output:
```
b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"
b1,abgr,lsb,xy      .. text: "E2A5q4E%uSA"
b2,b,lsb,xy         .. text: "AAPAAQTAAA"
b2,b,msb,xy         .. text: "HWUUUUUU"
b2,a,lsb,xy         .. file: Matlab v4 mat-file (little endian) >\004<\305P, numeric, rows 0, columns 0
b2,a,msb,xy         .. file: Matlab v4 mat-file (little endian) | <\243, numeric, rows 0, columns 0
b3,r,lsb,xy         .. file: gfxboot compiled html help file
b3p,r,lsb,xy        .. text: "Kooooooooohp"
b3p,b,lsb,xy        .. text: "!\" KKjONH4%"
b3p,b,msb,xy        .. text: ["R" repeated 10 times]
b3p,rgb,lsb,xy      .. text: "X~~[bb__Z~~[{f"
b3p,bgr,lsb,xy      .. text: "__zCC~~Z__z{G}_[["
b3p,abgr,lsb,xy     .. file: Hitachi SH big-endian COFF object file, no relocation info, no line number info, not stripped, 1 section, symbol offset=0x5050100, 67371264 symbols, optional header size 260, created Sun Jan  4 00:49:09 1970
b4,r,lsb,xy         .. file: Targa image data (16-273) 65536 x 4097 x 1 +4352 +4369 - 1-bit alpha - right "\021\020\001\001\021\021\001\001\021\021\001"
b4,g,lsb,xy         .. file: 0420 Alliant virtual executable not stripped
b4,b,lsb,xy         .. file: Targa image data - Map 272 x 17 x 16 +257 +272 - 1-bit alpha "\020\001\021\001\021\020\020\001\020\001\020\001"
b4,bgr,lsb,xy       .. file: Targa image data - Map 273 x 272 x 16 +1 +4113 - 1-bit alpha "\020\001\001\001"
b4,rgba,lsb,xy      .. file: Novell LANalyzer capture file
b4,rgba,msb,xy      .. file: Applesoft BASIC program data, first line number 8
b4,abgr,lsb,xy      .. file: Novell LANalyzer capture file
b5p,r,lsb,xy        .. file: Targa image data - Map (8-265) - RLE 65536 x 2049 x 1 +2304 +2313 - 9-bit alpha "\011\010\001\001\011\011\001\001\011\011\001"
b5p,r,msb,xy        .. file: tar archive (old), type '@' \200\200\220\020, uid  \200, gid \002\01, seconds @\010 \200, linkname \010
b5p,g,lsb,xy        .. file: PDP-11 pure executable not stripped - version 9
b5p,b,lsb,xy        .. file: Targa image data - Map 264 x 9 x 8 +257 +264 - 1-bit alpha "\010\001\011\001\011\010\010\001\010\001\010\001"
b5p,rgb,lsb,xy      .. file: , SYS \001\001\001\011\010
b5p,rgb,msb,xy      .. file: tar archive (old), type '@' \200\020, uid  \200, gid \002\01, seconds @\010 \200, linkname \010
b5p,bgr,lsb,xy      .. text: "I@FWW^PP__VWW^^Q_WVVFIj"
b5p,bgr,msb,xy      .. file: tar archive (old), type '@' \220, mode \020\02, uid  \200, gid \002\01, seconds @\010 \200, linkname \010
b6,rgb,lsb,xy       .. file: GLS_BINARY_MSB_FIRST
b6,rgb,msb,xy       .. file: Applesoft BASIC program data, first line number 130
b6,bgr,lsb,xy       .. file: GLS_BINARY_LSB_FIRST
b6,abgr,msb,xy      .. file: Applesoft BASIC program data, first line number 2
b6p,r,lsb,xy        .. file: PDP-11 UNIX/RT ldp
b6p,b,lsb,xy        .. text: "i *.+.*/+*(%"
b6p,rgb,lsb,xy      .. file: shared library
b6p,bgr,lsb,xy      .. file: Hitachi SH big-endian COFF object file, no relocation info, no line number info, not stripped, 1 section, symbol offset=0x5050100, 67371264 symbols, optional header size 260, created Sun Jan  4 00:49:09 1970
b7,r,lsb,xy         .. file: TTComp archive data, binary, 1K dictionary
b7,rgb,lsb,xy       .. file: TTComp archive data, binary, 1K dictionary
b7,rgba,lsb,xy      .. file: TTComp archive data, binary, 1K dictionary
b7,abgr,lsb,xy      .. file: TTComp archive data, binary, 1K dictionary
b7p,r,lsb,xy        .. file: Targa image data - Mono (2-259) 65536 x 513 x 1 +768 +771 - 3-bit alpha "\003\002\001\001\003\003\001\001\003\003\001"
b7p,g,lsb,xy        .. text: "'@?<A>?<C><B"
b7p,b,lsb,xy        .. file: GTA script (SCM), used in GTA III/VC/SA
b8,bgr,lsb,xy       .. file: PDP-11 UNIX/RT ldp
b8,rgba,lsb,xy      .. file: Targa image data - Map (256-0) 257 x 65536 x 1
b8,abgr,lsb,xy      .. file: Windows Precompiled iNF, version 1.0, InfStyle 1, flags 0x1000000, at 0x1000100, WinDirPath "",, LanguageID 101, at 0x1000100, at 0x1000000
b2,g,lsb,xy,prime   .. file: 0421 Alliant compact executable
b2,bgr,msb,xy,prime .. file: MacBinary, Wed Jan 25 21:19:20 2023, modified Mon Feb  6 11:58:16 2040 "*\240(\250\252\210\200\242\210\202", at 0x80 6354557 bytes resource
b2,abgr,lsb,xy,prime.. file: TTComp archive data, binary, 2K dictionary
b3,b,msb,xy,prime   .. file: MacBinary, char. code 0x4, Mon Feb  6 11:58:16 2040 INVALID date, modified Mon Feb  6 11:58:16 2040 "\222$@\002\004\011\331%\001"
b3,bgr,lsb,xy,prime .. file: MacBinary, Mon Feb  6 11:58:16 2040 INVALID date, modified Mon Feb  6 11:58:16 2040 "H$"
b3,rgba,lsb,xy,prime.. file: MacBinary, Mon Feb  6 11:58:16 2040 INVALID date, modified Mon Feb  6 11:58:16 2040 "@ "
b3p,bgr,lsb,xy,prime.. file: TTComp archive data, binary, 2K dictionary
b3p,abgr,lsb,xy,prime.. file: raw G3 (Group 3) FAX, byte-padded
b4,r,lsb,xy,prime   .. file: Novell LANalyzer capture file
b4,g,lsb,xy,prime   .. file: PDP-11 UNIX/RT ldp
b4,rgb,lsb,xy,prime .. file: Targa image data (4112-4113) 4369 x 257 x 1 +1 +4369
b4,abgr,lsb,xy,prime.. file: TeX font metric data (\020)
b5,g,msb,xy,prime   .. file: Intel ia64 COFF object file, not stripped, 8 sections, symbol offset=0x100400, 142605824 symbols, optional header size 64, created Wed Feb 18 14:15:28 1970
b5,b,lsb,xy,prime   .. file: Intel ia64 COFF object file, not stripped, 1040 sections, symbol offset=0x2080084, 1751853328 symbols, optional header size 66, created Wed Feb 18 13:39:45 1970
b5p,r,lsb,xy,prime  .. file: , SYS \011
b5p,g,lsb,xy,prime  .. file: PDP-11 UNIX/RT ldp
b5p,bgr,lsb,xy,prime.. file: raw G3 (Group 3) FAX, byte-padded
b5p,abgr,lsb,xy,prime.. file: Targa image data - Map 257 x 65536 x 1 +257
b6,r,lsb,xy,prime   .. file: MacBinary, Sat Jan  9 02:03:04 2066 INVALID date, modified Mon Feb  6 11:58:16 2040 "@\004\020\001\004\020\001\004\020A", at 0x80 344844 bytes resource
b6,g,msb,xy,prime   .. file: Applesoft BASIC program data, first line number 128
b6,rgb,lsb,xy,prime .. file: Targa image data - Map 4096 x 1024 x 16 +1089 +256 - 1-bit alpha - interleave
b6,bgr,lsb,xy,prime .. file: X11 SNF font data, MSB first
b6,rgba,lsb,xy,prime.. file: X11 SNF font data, MSB first
b6p,r,lsb,xy,prime  .. file: shared library
b6p,g,lsb,xy,prime  .. file: PDP-11 UNIX/RT ldp
b6p,b,lsb,xy,prime  .. file: TTComp archive data, binary, 2K dictionary
b6p,rgb,lsb,xy,prime.. file: TTComp archive data, binary, 2K dictionary
b6p,bgr,lsb,xy,prime.. file: raw G3 (Group 3) FAX, byte-padded
b6p,abgr,lsb,xy,prime.. file: Targa image data - Map 257 x 65536 x 1 +257
b7,b,lsb,xy,prime   .. file: Targa image data - RLE 64 x 2 x 8 +4 +8192 - right
b7,a,lsb,xy,prime   .. file: Matlab v4 mat-file (little endian) ?2, numeric, rows 0, columns 0
b7,a,msb,xy,prime   .. file: Matlab v4 mat-file (little endian) \374L, numeric, rows 0, columns 0
b7p,g,lsb,xy,prime  .. file: PDP-11 UNIX/RT ldp
b7p,bgr,lsb,xy,prime.. file: raw G3 (Group 3) FAX, byte-padded
b7p,abgr,lsb,xy,prime.. file: Targa image data - Map 257 x 65536 x 1 +257
b8,r,lsb,xy,prime   .. file: raw G3 (Group 3) FAX, byte-padded
b8,b,lsb,xy,prime   .. file: Targa image data - Map 257 x 65536 x 1 +257
b1,bgr,lsb,yx       .. /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s': stack level too deep (SystemStackError)
        from /var/lib/gems/3.0.0/gems/iostruct-0.3.0/lib/iostruct.rb:171:in `inspect'
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.0.0/gems/iostruct-0.3.0/lib/iostruct.rb:171:in `inspect'
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.0.0/gems/iostruct-0.3.0/lib/iostruct.rb:171:in `inspect'
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.0.0/gems/iostruct-0.3.0/lib/iostruct.rb:171:in `inspect'
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
         ... 10906 levels...
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.0.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'
```

The file is found in the ```b1,rgb,lsb,xy``` part of the image:
```
picoCTF{7h3r3_15_n0_5p00n_a1062667}
```

