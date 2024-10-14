# Processes and Jobs

## Challenge 1: **Listing Processes**
This challenge deals with understanding the use of the ```ps``` command to list running processes. It also explains the use of its arguments: ```ps -ef``` and ```ps aux``` and the differences between their outputs.

### Steps involved in approaching the challenge:
1. To list the running processes the following command is run:
```
ps -ef
```
2. The following output is displayed:
```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:34 ?        00:00:00 /sbin/docker-init -- /nix/va
root           7       1  0 12:34 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 12:34 ?        00:00:00 /challenge/767-run-20530
root          72      68  0 12:34 ?        00:00:00 sleep 6h
hacker        95       1  0 12:34 ?        00:00:00 /nix/store/g53lqy8w86jkp2g98
hacker       100       1  0 12:34 ?        00:00:00 /nix/store/1xhds5s320nfp2022
hacker       108     100  0 12:34 ?        00:00:00 /nix/store/3wb0055984n2whn44
hacker       119       1  0 12:34 ?        00:00:00 /nix/store/jnz1wdn463qilzhc8
hacker       122       1  0 12:34 ?        00:00:00 /nix/store/rvr416z148cjcxh2b
hacker       123       1  0 12:34 ?        00:00:00 /run/current-system/sw/bin/d
hacker       128       1  0 12:34 ?        00:00:00 /nix/store/3zi7zn2bbz3jpx8ds
hacker       137       1  0 12:34 ?        00:00:00 /run/workspace/bin/ssh-agent
hacker       139     119  0 12:34 ?        00:00:00 xfwm4
hacker       145     119  0 12:34 ?        00:00:00 xfsettingsd
hacker       149     119  0 12:34 ?        00:00:01 xfce4-panel
hacker       154     119  0 12:34 ?        00:00:00 Thunar --daemon
hacker       168     119  0 12:34 ?        00:00:00 xfdesktop
hacker       183     149  0 12:34 ?        00:00:00 /nix/store/xpgf309sv9w5majf2
hacker       187     149  0 12:34 ?        00:00:00 /nix/store/xpgf309sv9w5majf2
hacker       295     108  0 12:35 ?        00:00:00 /nix/store/3wb0055984n2whn44
hacker      1278       1  0 12:39 ?        00:00:00 /run/workspace/bin/xfce4-mim
hacker      1279    1278  5 12:39 ?        00:00:00 /run/workspace/bin/xfce4-ter
hacker      1285    1279  0 12:39 pts/0    00:00:00 bash
hacker      1315    1285  0 12:39 pts/0    00:00:00 ps -ef

```
3. As explained in the prompt, ```docker-init```, ```sleep 6h``` are system related processes.
4. Ignoring those, the process likely to contain the flag is:
```
/challenge/767-run-20530
```

### Flag Generation:
*  Thus for flag generation, the program is reinitialized using:
```
/challenge/767-run-20530
```
* The following output is generated:
```
Yahaha, you found me! Here is your flag:
pwn.college{8E9cjCaZuYSzzspEQX5Ktrq2Qp1.dhzM4QDL2MTO0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Killing Processes**
This challenge involves understanding the use of the ```kill``` command to terminate a currently running process.

### Steps involved in approaching the challenge:
1. To locate the process that needs to be killed, we find the process still running currently using ```sleep```.
2. Thus we ```grep``` for it and pipeline it using the following command:
```
ps -e | grep sleep
```
3. Thus this lists all the currently running processes with ```sleep```.
```
    74 ?        00:00:00 sleep
```
4. Thus we have located the process that needs to be killed: ```74```
5. The following command is run:
```
kill 74
```
6. On redoing step 2 no output is generated, so we have successfull killed the process.

### Flag Generation:
* Thw following command should generate the flag after killing ```74```:
```
/challenge/run
```
* The following output is generated:
```
Great job! Here is your payment:
pwn.college{cQrGLp9tqguJq6X3QhqTOpmxhme.dJDN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
