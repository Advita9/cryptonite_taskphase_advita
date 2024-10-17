# Chaining Commands

## Challenge 1: **Chaining with Semicolons**
This challenge involves understanding the use of ```;``` to chain commands and separate them similiar to Enter.

### Steps involved in approaching the challenge:
1. The prompt states that ```/challenge/pwn``` and ```/challenge/college``` need to be chained together.

## Flag Generation:
* The following command is used to generate the flag:
```
/challenge/pwn; /challenge/college
```
* The following output is generated:
```
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gVcPo2pKQdFknf7smsCW4nlzfXU.dVTN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Your First Shell Script**
This challenge involves understanding how to create a shell script with the default ```.sh``` extension.

### Steps involved in approaching the challenge:
1. We need to run the same commands as challenge 1, but using a shell script called ```x.sh```
2. Using the VSCode workspace, a file called ```x.sh``` is created with the following text:
```
/challenge/pwn; /challenge/college
```
3. We return to the terminal to run the file using ```bash```.

### Flag Generation:
* The following command is used to invoke the file:
```
bash x.sh
```
* The following output is generated:
```
Great job, you've written your first shell script! Here is the flag:
pwn.college{cCsZ38LMmExdNZWs1Aul5ZELJvg.dFzN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 3: **Redirecting Script Output**
This challenge involves understanding how to pipe from a script into another program.

### Steps involved in approaching the challenge:
1. We need to run the same commands as challenge 1, but using a shell script called ```x.sh```
2. Using the VSCode workspace, a file called ```x.sh``` is created with the following text:
```
/challenge/pwn; /challenge/college
```
3. We return to the terminal to run the file using ```bash``` and redirect it into ```/challenge/solve```

### Flag Generation:
* The following command is run to generate the flag:
```
bash x.sh | /challenge/solve
```

* The following output is generated:
```
Correct! Here is your flag:
pwn.college{MtByl-s4x5vqaCcx3952-p5MwUm.dhTM5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Executable Shell Scripts**
This challenge involves understanding how to call a shell script directly without using ```bash``` by first making it executable by changing permissions.

### Steps involved in approaching the challenge:
1. The prompt states that first a shellscript invoking ```/challenge/solve``` needs to be created, and it has to be invoked without ```bash``` in the terminal.
2. In the VSCode workspace, a file ```x.sh``` is created with the following content:
```
/challenge/solve
```
3. We return to the terminal to change permissions.
4. The following command is used to make the script executable:
```
chmod a+x x.sh
```
### Flag Generation:
* The following command is used to invoke the script without ```bash```:
```
/home/hacker/x.sh
```
* The following output is generated:
```
Congratulations on your shell script execution! Your flag:
pwn.college{QSjVNVabiJLCyl8Hk3ffcj0zRvY.dRzNyUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.



