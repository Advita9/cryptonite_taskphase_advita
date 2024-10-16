# Untangling Users

## Challenge 1: **Becoming root with su**
This challenge involves understanding the use of the **Switch user** command ```su``` to start a root shell.

### Steps involved in approaching the challenge:
1. The prompt states that the password to provide ```su``` is ```hack-the--planet```.
2. The ```su``` command is called.
3. The password is provided.
4. The shell switches to ```root@users-becoming-root-with-su:/home/hacker```.

### Flag Generation:
* After successfully switching the user, the flag is read using:
```
cat /flag
```
* The following output is generated:
```
pwn.college{893EdE1gJOjlqOHMCWBLcff58W9.dVTN0UDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


