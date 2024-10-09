# File Globbing

## Challenge 1: Matching with *

This challenge involves understanding the use of * as a **wildcard** to replace that argument with any files that match the pattern.

### Steps involved in approaching the challenge:
1. The prompt states that we need to navigate to the ```/challenge``` directory using at most 3 characters in the argument passed to ```cd```.
2. Follosing the prompt, the following command is run:
```cd /*ge```

### Flag Generation:
* The command leads the directory to change to ```/challenge```.
* The following command is run:
```
/challenge/run
```
* The following output is generated:
```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kB6MZRQG85mP5UZAtsBV6ssrKyT.dFjM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Matching with ?**

This challenge involves understanding the use of ```?``` as a single character wildcard.

### Steps involved in approaching the challenge:
1. The prompt states that we need to navigate to the ```/challenge``` directory using ```?``` character instead of c and l in the argument to ```cd```.
2. The following command is run:
```
cd /?ha??enge
```

### Flag Generation:
* The command leads the directory to change to ```/challenge```.
* The following command is run for flag generation:
```
/challenge/run
```
* The following output is generated:
```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{AYZUfDAqJAg2ApdhBsOq-DFnA1b.dJjM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 3: **Matching with []**

This challenge involves understanding the use of ```[]``` as a wildcard for some subset of petential characters.

### Steps involved in approaching the challenge:
1. The prompt states that we need to first navigate into ```/challenge/files```. The following command is used:
```
cd /challenge/files
```
2. Next, the ```/challenge/run``` command needs to be run with one argument using ```[]``` for four files.

### Flag Generation:
* Based on the prompt, the following command is run for flag generation:
```
/challenge/run file_[absh]
```
* The following output is generated:
```
You got it! Here is your flag!
pwn.college{UJ65tC9unqLd8M76BnwfcxIqKK_.dNjM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Matching paths with []**

This challenge involves understanding the use of ```[]``` to expand entire paths in the arguments.

### Steps involved in approaching the challenge:
1. The prompt states that we need to access files in the ```/challenge/files``` directory by globbing their absolute paths.
2. The prompt states that we need to run ```/challenge/run``` with a single argument from the home directory.

### Flag Generation:
* Based on the above instructions, the folloeing command is run for flag generation:
```
/challenge/run /home/hacker/challenge/files/file_[absh]
```
* The following output is generated:
```
You got it! Here is your flag!
pwn.college{4IxfRsrafJLWvtcgrEPU3-m_hIV.dRjM4QDL2MTO0czW}

```

## Challenge 6: **Exclusionary Globbing**
This challenge involves understanding the use of ```[]``` to filter files out in a glob and invert if that bracket instance matches characters listed.

### Steps involved in approaching the challenge:
1. The prompt states that we need to navigate to the ```/challenge/files``` directory:
```
cd /challenge/files
```
2. To generate the flag, the ```/challenge/run``` command needs to be run along with the files not starting witj p, w or n.

### Flag Generation:
* Based on the above instructions, the following command is run:
```
/challenge/run [!pwn]*
```
* The following output is generated:
```
You got it! Here is your flag!
pwn.college{ML3x70y8WuDcvJ9dPu-3heCV8Lb.dZjM4QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
