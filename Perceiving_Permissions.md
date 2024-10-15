# Perceiving Permissions

## Challenge 1: **Changing File Ownership**
This challenge involves understanding the use of ```chown``` to change the ownership pf files.

### Steps involved in approaching the challenge:
1. The prompt states that for this particular challenge, we as the ```hacker``` will be allowed to change file permissions using ```chown```.
2. We need to change permissions for the ```/flag``` file.
3. The following command is used:
```
chown hacker /flag
```

### Flag Generation:
* The following command is used to generate the flag after successfully changing the file permissions:
```
cat /flag
```
* The following output is generated:
```
pwn.college{YXk4GZ70LDvGo3u9MZhYdHPt6IP.dFTM2QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
