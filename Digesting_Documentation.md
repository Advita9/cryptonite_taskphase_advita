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
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


## Challenge 3: **Reading Manuals**

This challenge involves understanding the use of the ```man``` command, used to display the manual of the command passed as an argument.

### Steps involved in approaching the challenge:
1. The prompt states that the flag will be displayed through a command mentioned in the documentation for the ```challenge``` command.
2. Thus the following command is typed:
```man challenge```
The following output is generated:
```
CHALLENGE(1)                  Challenge Commands                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --rfxyif NUM
              print the flag if NUM is 597

AUTHOR
       Written by Zardus.
```
3. Understanding the documentation:
* ```/challenge/challenge```: Needs to be used to print the flag
* ```--rfxyif NUM```: is the argument that needs to be used to print the flag with NUM = 597

### Flag Generation:
* Based on the documentation and correct syntax for the command, the following is used:
```
/challenge/challenge --rfxyif 597
```
* The following output is generated:
```
Correct usage! Your flag: pwn.college{UCrfUWx5GWCZXyIN9i7FfOF0KVb.dRTM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Searching Manuals**

This challenge involves understanding how to search through a manual using specific keys.

### Steps involved in approaching the challenge:
1. Reading the documentation for ```challenge``` using the following command:
```
man challenge
```
2. A long documentation page is displayed.
3. The ```/flag``` command is typed to search for occurences of ```flag``` in the documentation.
4. The ```n``` key is used to go through all occurences.
5. Useful information found:
```
/challenge/challenge - print the flag!
```
```
DESCRIPTION
       Output the flag when called with the right argument.
```
6. The correct argument is found:
```
-r     This argument will give you the flag!
```
7. The ```q``` key is used to quit the documentation page.

### Flag Generation:
* The following command is used for generating the flag, after bringing together the correct command and argument from the documentation:
```
/challenge/challenge -r
```
* The following output is generated:
```
Initializing...
Correct usage! Your flag: pwn.college{owJbpVBILoptt6XbwiXCKYba8_i.dVTM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
```

## Challenge 5: **Searching for Manuals**

## Challenge 6: **Helpful Programs**

This challenge involves understanding the use of ```--help``` or ```-h``` to find information about programs that do not have a manual page associated with them.

### Steps involved in approaching the challenge:
1. The following command is used to look up information about the ```/challenge/challenge``` command:
```
/challenge/challenge --help
```
2. The following output is generated:
```
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give
                        you the flag
```

3. Understanding the documentation:
* ```-g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value```
This command needs to be used for flag generation. However the ```GIVE_THE_FLAG``` value is missing.
* ```-p, --print-value     print the value that will cause the -g option to give
                        you the flag```
This command needs to be used to find the missing value. 

4. The following command is then used for generating the missing value:
```
/challenge/challenge --p
```
The following output is generated:
```
The secret value is: 55
```

### Flag Generation:
* Putting together the information obtained from the ```-h``` page of the ```/challenge/challenge``` command, the following command is used for flag generation:
```
/challenge/challenge --g 55
```
* The following output is generated:
```
Correct usage! Your flag: pwn.college{oBgPjUzLYLfm0ADg5e5ZQDHf8k9.ddjM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 7: **Help for Builtins**

This challenge involves understanding how to access information about the third type of programs: **built-in shell programs**. 

### Steps involved in approaching the challenge:
1. The challenge prompt states that the ```challenge``` command is a shell built-in for this challenge, instead of a program. 
2. Thus the ```help``` command is used to acces its utility:
```
help challenge
```
The following output is generated:
```
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "M7mlAeVV".
```
3. Looking at the information, it is clear that the correct argument to be used for flag generation is:
```
--secret SECRET
```
The value of ```SECRET``` needs to be deciphered.
4. Reading ahead, the correct value for the ```--secret``` argument is stated:
```
M7mlAeVV
```

### Flag Generation:
* Putting together information from above, the following command is used for flag generation.
```
challenge --secret M7mlAeVV
```
* The following output is generated:
```
Correct! Here is your flag!
pwn.college{M7mlAeVVp9vj5--gYMJ40YMD4hw.dRTM5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

