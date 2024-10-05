# Digesting Documentation

## Challenge 1: **Learning From Documentation**

This challenge involves an introduction to understanding the concept of reading documentation.

### Steps involved in approaching the challenge:
1. Reading the challenge prompt gives an understnading of the flag invocation through the ```/challenge/challenge``` command.
2. Further, it states that the argument to be added in order to correctly invoke the flag is ```--giveflag```.

### Flag Generation:
* Understanding the challenge prompt correctly and applying that to the syntax of a command and its argument, the following command is typed in the command line to generate the flag:
```
/challenge/challenge --giveflag
```
* The following output is generated:
```
Correct argument! Here is your flag:
pwn.college{YbEZfp2lJlh7vxskP50H3lgH1Mr.dRjM5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Learning Complex Usage**
This challenge is an extension to reading documentation, and deals with understanding slightly more complex instructions.

### Steps involved in approaching the challenge:
1. On reading the documentation for ```/challenge/challenge``` it can be inferred that the ```--printfile``` argument will need to be used to print an arbitrary file containing the flag for the challenge.
2. The next step involves finding out the file that contains the flag and needs to be printed.
This is done using the ```ls``` command to list out all the files in the directory.
The following output is obtained:
```
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var

```
3. The flag file is present. On trying to read the file directly using the ```cat /flag``` command, the following output is generated:
```
cat: flag: Permission denied
```
4. Thus this implies we will need to use ```/challenge/challenge``` with appropriate arguments to access the flag.
5. Understanding the syntax provided in the documentation, it is inferred that the ```/challenge/challenge``` command needs to be used with the ```--printfile``` argument, and the path of the file to be read is ```/flag```

### Flag generation:
* Based on the previous understanding, the following command is used for flag generation:
```
/challenge/challenge --printfile /flag
```
* The following output is generated:
```
Correct argument! Here is the /flag file:
pwn.college{EaDCukKeudCz-yxn8UBIRbSF_R9.dVjM5QDL2MTO0czW}
```
