## ARMssembly 1

Challenge description:
```
For what argument does this program print `win` with variables 58, 2 and 3? File: chall_1.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})
```

Hint:
```
Shifts
```

The provided file link is :
```
https://mercury.picoctf.net/static/1c8d50e39cf00d144e6a72119f68c16c/chall_1.S
```

The contents of the file:
```
        .arch armv8-a
        .file   "chall_1.c"
        .text
        .align  2
        .global func
        .type   func, %function
func:
        sub     sp, sp, #32
        str     w0, [sp, 12]
        mov     w0, 58
        str     w0, [sp, 16]
        mov     w0, 2
        str     w0, [sp, 20]
        mov     w0, 3
        str     w0, [sp, 24]
        ldr     w0, [sp, 20]
        ldr     w1, [sp, 16]
        lsl     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 24]
        sdiv    w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 12]
        sub     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w0, [sp, 28]
        add     sp, sp, 32
        ret
        .size   func, .-func
        .section        .rodata
        .align  3
.LC0:
        .string "You win!"
        .align  3
.LC1:
        .string "You Lose :("
        .text
        .align  2
        .global main
        .type   main, %function
main:
        stp     x29, x30, [sp, -48]!
        add     x29, sp, 0
        str     w0, [x29, 28]
        str     x1, [x29, 16]
        ldr     x0, [x29, 16]
        add     x0, x0, 8
        ldr     x0, [x0]
        bl      atoi
        str     w0, [x29, 44]
        ldr     w0, [x29, 44]
        bl      func
        cmp     w0, 0
        bne     .L4
        adrp    x0, .LC0
        add     x0, x0, :lo12:.LC0
        bl      puts
        b       .L6
.L4:
        adrp    x0, .LC1
        add     x0, x0, :lo12:.LC1
        bl      puts
.L6:
        nop
        ldp     x29, x30, [sp], 48
        ret
        .size   main, .-main
        .ident  "GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
        .section        .note.GNU-stack,"",@progbits
```


Understanding the assembly code:

* The main function reads user argument and stores it.
* Then it is converted to integer using atoi function.
* This integer is passed to the func function via register w0.
* After function execution, the return value is compared to 0. If it is 0, it prints ```You win!```. Otherwise, it prints ```You Lose :(```.
* Thus to reverse engineer, we need to find user input to get 0 as return value.

* Inside func the stack layout is:
```
[sp + 12] = user_input (initially w0)
[sp + 16] = 58
[sp + 20] = 2
[sp + 24] = 3
```
* The bitwise and arithmetic operations performed are:
1. left shift by 2.
58 in binary- 111010
After left shift operation- 11101000 
Integer equivalent- 232

2. Integer division by 3
232 / 3 = 77

3. Subtraction of 77 - user input


* Based on above steps we need to find :
```
77 - user input = 0
```
Thus user input should be 77.

* According to flag format description, it should be in hex format.

Thus final flag is:
```
picoCTF{0000004d} 
```
