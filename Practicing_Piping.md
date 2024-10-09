# Practicing Piping

## Challenge 1: **Redirecting output**
This challenge involves understanding the use of ```>``` to redirect output to the file after it.

### Steps involved in approaching the challenge:
1. The prompt states that input redirection needs to be used to write ```PWN``` to the file ```COLLEGE```.

### Flag generation:
* Based on the prompt, the following command is run:
```
echo PWN > COLLEGE
```
* The following output is generated:
```
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{s0p_PGlHNafHwiVACiO6xrGG_q2.dRjN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Redirecting more output**
This challenge involves redirecting output of a directory/command to a file.

### Steps involved in approaching the challenge:
1. The challenge prompt states that the output of ```/challenge/run``` needs to be redirected to the file ```myflag```
2. Thus the following command is run:
```
/challenge/run > myflag
```
3. The following output is generated:
```
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
```

### Flag Generation:
* Based on the prompt, the following command is run for flag generation to read the contents of ```myflag```:
```
cat myflag
```
* The following output is generated:
```
[FLAG] Here is your flag:
[FLAG] pwn.college{AW6k97LEyrQmPeVqQBtrYFsrycK.dVjN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


## Challenge 3: **Appending output**
This challenge involves understanding how to **append** output using ```>>``` instead of just overwriting it.

### Steps involved in approaching the challenge:
1. The challenge prompt states that we need to redirect the output of ```/challenge/run``` to ```/home/hacker/the-flag``` using the append-mode redirect.
2. The following command is used:
```
/challenge/run >> /home/hacker/the-flag
```
3. The following output is generated:
```
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
```

### Flag Generation:
* Based on the instructions, the following command is used to read the contents of ```the-flag```:
```
cat /home/hacker/the-flag
```
* The following output is generated:
```
 | 
\|/ This is the first half:
 v 
pwn.college{ozvGWrpcM22JS9mx5IG3VOqnIct.ddDM5QDL2MTO0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```

Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Redirecting Errors**
This challenge involves understanding how to redirect not just standard output but also standard error and standard input.

### Steps involved in approaching the challenge:
1. The prompt states that the Standard Output of ```/challenge/run``` needs to be directed into ```myflag``` and the errors need to be directed into ```instructions```.
2. Based on the instructions, the following command is run:
```
/challenge/run > myflag 2> intructions
```
### Flag Generation:
* Once redirected, the following command is run to read the contents of ```myflag```.
```
cat myflag
```
* The following output is generated:
```
[FLAG] Here is your flag:
[FLAG] pwn.college{0jUnQnnTlstNkFQvcnahoCOU24b.ddjN1QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 5: **Redirecting input**
This challenge involves understanding how to redirect input using ```<```.

### Steps involved in approaching the challenge:
1. The prompt states that the ```PWN``` file needs to contain the value ```COLLEGE```. The following command is run:
```
echo COLLEGE > PWN
```
2. The next step involves redirecting the input from ```PWN``` to  ```/challenge/run```.

### Flag Generation:
* Based on the prompt, the following command is run for flag generation:
```
/challenge/run < PWN
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

