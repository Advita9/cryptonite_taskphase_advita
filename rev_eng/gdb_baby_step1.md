## GDB baby step 1

1. The gdb debugger is installed using ```sudo apt install gdb```

2. The challenge prompt states:
```
Description
Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.
```

Hints are:
```
gdb is a very good debugger to use for this problem and many others!
main is actually a recognized symbol that can be used with gdb commands.
```

3. The file is extracted from the link on terminal:
```
wget https://artifacts.picoctf.net/c/512/debugger0_a
```
4. To display info about the file:
```
file debugger0_a
```

5. To start debugging it:
```
gdb debugger0_a
```

6. Output:
```
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from debugger0_a...
(No debugging symbols found in debugger0_a)
```

7. To find out about functions in the file:
```
info function
```
8. Output:
```
(gdb) info function
All defined functions:

Non-debugging symbols:
0x0000000000001000  _init
0x0000000000001030  __cxa_finalize@plt
0x0000000000001040  _start
0x0000000000001070  deregister_tm_clones
0x00000000000010a0  register_tm_clones
0x00000000000010e0  __do_global_dtors_aux
0x0000000000001120  frame_dummy
0x0000000000001129  main
0x0000000000001140  __libc_csu_init
0x00000000000011b0  __libc_csu_fini
0x00000000000011b8  _fini
```

9. Looking at the output, main is one of the functions. From the hint, we can use ```main``` directly as a command:
```
disassemble main
```
10. Output:
```
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   %rbp
   0x000000000000112e <+5>:     mov    %rsp,%rbp
   0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    mov    $0x86342,%eax
   0x000000000000113d <+20>:    pop    %rbp
   0x000000000000113e <+21>:    ret
End of assembler dump.
```

11. The ```eax``` register has value ```0x86342```. We can print the value in decimal using:
```
print 0x86342
```

12. Output:
```
(gdb) print 0x86342
$1 = 549698
```

13. Based on challenge instructions, the following is the flag:
```
picoCTF{549698}
```



