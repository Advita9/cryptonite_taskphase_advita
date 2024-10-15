# Perceiving Permissions

## Challenge 1: **Changing File Ownership**
This challenge involves understanding the use of ```chown``` to change the ownership of files.

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

## Challenge 2: **Groups and Files**
This challenge involves understanding the use of ```chgrp``` to change the group ownership of files.

### Steps involved in approaching the challenge:
1. The prompt states that for this particular challenge, we as the ```hacker``` will be allowed to change file permissions using ```chgrp```.
2. We need to change group permissions for the ```/flag``` file.
3. The following command is used:
```
chgrp hacker /flag
```

### Flag Generation:
* The following command is used to generate the flag after successfully changing the file permissions:
```
cat /flag
```
* The following output is generated:
```
pwn.college{UAV1HF4LsrcW7iv7Xvq8QKLkZDL.dFzNyUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 3: **Fun with Groups Names**
This challenge involves finding out the group our user is in and then changing the group permissions accordingly.

### Steps involved in approaching the challenge:
1. The firts step involves using ```id``` to list the available groups.
2. The following output is generated:
```
uid=1000(hacker) gid=1000(grp627) groups=1000(grp627)
```
3. Thus, the group other than ```hacker``` is ```grp627```.
4. The following command is used to change group:
```
chgrp grp627 /flag
```

### Flag Generation:
* After successfully changing group permissions, the following command is run to print the flag:
```
cat /flag
```
* The following output is generated:
```
pwn.college{w4sWVB_SeIaxjr461D4xltdEttT.dJzNyUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Changing Permissions**
This challenge involves understanding how to change file permission using ```chmod```.

### Steps involved in approaching the challenge:
1. The prompt states that permissions need to be changed for the ```flag``` file.
2. To check the current status, the following command is used:
```
ls -l /flag
```
3. The following output is generated:
```
-r-------- 1 root root 58 Oct 15 17:03 /flag

```
Thus currently there is read permission for the root.
4. To change permissions, the file needs to be made accessible to either other users using ```o``` or ***all** users using ```a```.
5. One of the two commands is used:
```
chmod a+r /flag

chmod o+r /flag
```
6. The updated permission is checked using:
```
ls -l flag
```
7. The following output is generated:
```
-r--r--r-- 1 root root 58 Oct 15 17:03 /flag

```

### Flag Generation:
* After changing permissions, ```/flag``` file can be read using:
```
cat /flag
```
* The following output is generated:
```
pwn.college{EhMt4br5ImNoci88o5PEs8JXxrZ.dNzNyUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
