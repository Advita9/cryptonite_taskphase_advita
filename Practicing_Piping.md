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
'''
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



