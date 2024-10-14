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

## Challenge 3: **Interrupting Processes**
This challenge involves understanding the use of ```Ctrl+C``` to interrupt an application and cause it to exit.

### Steps involved in approaching the challenge:
1. The first step, according to the prompt is getting the program to run, using the following command:
```
/challenge/run
```
2. The following output is generated:
```
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
```
### Flag Generation:
* The ```Ctrl+C``` keys are pressed to end the process:
* The following output is generated:
```
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{01CRNss1FYM0BXeXIJNBgeWbuNf.dNDN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Suspending Processes**
This challenge involves understanding the use of ```Ctrl-Z``` to suspend a process instead of entirely terminating it.

### Steps involved in approaching the challenge:
1. The first step again involves running the program using the following command:
```
/challenge/run
```
2. The following output is generated:
```
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         429     354  0 16:36 pts/0    00:00:00 bash /challenge/run
root         431     429  0 16:36 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
```
### Flag Generation:
* The following command is run to re-initialize the process with the first one temporarily suspended:
```
/challenge/run
```
* The following output is generated:
```
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         429     354  0 16:36 pts/0    00:00:00 bash /challenge/run
root         490     354  0 16:36 pts/0    00:00:00 bash /challenge/run
root         492     490  0 16:36 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{clzbp7Y_x430DwcoCYzvphB9qps.dVDN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 5: **Resuming Processes**
This challenge involves understanding how to resume a suspended process, using the ```fg command```.

### Steps involved in approaching the challenge:
1. The following command is run to initialize the process:
```
/challenge/run
```
2. The following output is generated:
```
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
```
3. The ```Ctrl+Z``` keys are used to suspend the process.

### Flag Generation:
* After successfully suspending the process, the following command is run to restart it:
```
fg
```
* The following output is generated:
```
/challenge/run
I'm back! Here's your flag:
pwn.college{IEibMoo0Xqcp2RDgpnokgQ7sHxu.dZDN4QDL2MTO0czW}
Don't forget to press Enter to quit me!

Goodbye!
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page. 

## Challenge 6: **Backgrounding Processes**
This challenge involves understanding how to resume a process in the background using the ```bg``` command.

### Steps involved in approaching the challenge:
1. The process is invoked using the following command:
```
/challenge/run
```
2. The following output is generated:
```
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         329 S+   bash /challenge/run
root         331 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
```
3. The ```Ctrl+Z``` keys are used to suspend the process.
4. The following command is run to send the process to the background and restart it there:
```
bg
```
5. The following output is generated:
```
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
```

### Flag Generation:
* The following command is run to restart to process while the first one runs in the background:
```
/challenge/run
```
* The following output is generated:
```
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         329 S    bash /challenge/run
root         359 S    sleep 6h
root         381 S+   bash /challenge/run
root         383 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{k401d_al5ZqVDJFlqSpxnuDBFrf.ddDN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 7: **Foregrounding Processes**
This challenge involves understanding how to foreground a backgrounded process using the ```fg``` command.

### Steps involved in approaching the challenge:
1. The following command is run to invoke the process:
```
/challenge/run
```
2. The following output is generated:
```
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run

```
3. The ```Ctrl+Z``` keys are used to suspend the process.
4. The following command is run to send the suspended process to the background:
```
bg
```
5. The following output is generated:
```
[1]+ /challenge/run &



hacker@processes~foregrounding-processes:~$ Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

```

### Flag Generation:
* The following command is run to bring the backgrounded process to the foreground:
```
fg
```
* The following output is generated:
```
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{ksL4GgBwD9tNQ0mKSKZxPltyivF.dhDN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 8: **Starting Backgrounded Processes**
This challenge involves understanding the use of ```&``` to start a process backgrounded from the very start.

### Steps involved in approaching the challenge:
1. The prompt explains that the ```&``` needs to be appended after the command to initiate it in the background.
2. The ```/challenge/run``` command needs to be run in the background.

### Flag Generation:
* The following command is run, following the syntax, for flag generation:
```
/challenge/run
```
* The following output is generated:
```
[1] 351
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{QuAft-brK8raQC1gJvuv-HOWr7Q.dlDN4QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 9: **Process Exit Codes**
This challenge involves understanding the use of ```$?``` to read the exit codes of a process.

### Steps involved in approaching the challenge:
1. The exit code of the ```/challenge/get-code``` process needs to be retreived.
2. The following code is run:
```
/challenge/get-code
```
3. The following output is generated:
```
Exiting with an error code!
```
4. To read the error code, the following command is used:
```
echo $?
```
5. The following output is generated:
```
104
```

### Flag Generation:
* Based on the prompt, the error code needs to be passed as an argument to the ```/challenge/submit-code``` program.
* Based on the syntax, the following command is run:
```
/challenge/submit-code 104
```
* The following output is generated:
```
CORRECT! Here is your flag:
pwn.college{0YZtJqn5DJAOhWx6H4UXZkE-Z66.dljN4UDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
