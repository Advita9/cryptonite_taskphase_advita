# Pondering Paths

## Challenge 1: **The Root**
This challenge is to invoke the pwn directory using the command:
```
/pwn
```
### Understanding the command:
* `/` backslash placed before the name of the file/directory.
* `pwn` the program to invoke to grant access to the flag for this challenge.
* `/pwn` understanding the meaning of an *absolute path* - one that starts with the root directory.

### Flag Generation:
On running the command the following terminal output was displayed:
```
BOOM!!!
Here is your flag:
pwn.college{IQCTyZb871USXd1E6h4nsDOzsUi.dhzN5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Program and absolute paths**
This challenge explores accessing a two-layer path. 
It involves accessing the ```/run``` directory placed inside the ```/challenge``` directory, which in turn lies inside root (concept of absolute path).

The command used to generate the flag:
```
/challenge/run
```

### Understanding the command:
* ```/challenge``` directory placed inside the root.
* ```/run``` the file with the challenge program. It needs to be accessed to get the flag. 
* ```/challenge/run``` is thus the absolute path of run.

### Flag Generation:
On running the command, the following terminal output was displayed:
```
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{Q6jBriMYwxaHKiv8cdz5MO5gJp0.dVDN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
