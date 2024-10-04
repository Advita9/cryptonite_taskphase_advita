# Comprehending Commands

## Challenge 1: **cat: not the pet, but the command!**

This challenge deals with understanding the use of the ```cat``` command on the command line.

### Steps involved in approaching the challenge:

1. Following the instructions in the challenge prompt signals that we need to read the contents of the flag file located in the home directory to access the flag.
2. The home directory as already learnt is the ```~``` default directory when the command line opens.
3. The ```ls``` command is typed to check the presence of the ```flag``` file in the home directory. The following output is generated:
```
Desktop  a  flag  leap
```
This confirms that flag is present and can be read using ```flag``` command.

### Flag Generation:
* The following command is typed into the command line at the ```~``` level:
```
cat flag
```

* The following output was generated:
```
pwn.college{AsJqMGItoa_RbhmBggHx1N8fNI-.dFzN1QDL2MTO0czW}
```

Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **catting absolute paths**

This challenge deals with understanding the use of the ```cat``` command when dealing with an absolute path as the argument instead of the file being located in the current/home directory.

### Steps involved in approaching the challenge:
1. The challenge prompt states that ```flag``` is not located in the home directory. To confirm this, the ```ls`` command is used to display the contents of the home directory, and the following output is generated:
```
Desktop  a  leap
```
This confirms that ```flag``` is not in the ```~``` directory.

2. Thus following the prompt, it implies that the absolute path needs to be used to access the flag.

### Flag Generation:
* The following command is typed in the ```~``` directory to access the absolute path of the ```flag``` file:
```
cat /flag
```
* The following output is generated:
```
pwn.college{4ERCyaeOJ9mC7pKxbJc1Qa2Ig94.dlTM5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 3: **more catting practice**

This challenge deals with the use of the ```cat``` command using an absolute path as an argument, with the constraint of **NOT** using the ```cd``` command.

### Steps involved in approaching the challenge:
1. The command line gives the following instructions:
```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/pyshared/flag. Go cat it out **without** cding into that 
directory!
```
2. This makes it clear about using the ```cat``` command with the ```/usr/share/pyshared/flag``` argument as the absolute path of the file to be read to access the flag.

### Flag Generation:
* The following command is typed:
```
cat /usr/share/pyshared/flag
```

* The following output is generated:
```
pwn.college{8w22BWQAiC7HIYY_eIHYgIqz4Ex.dBjM5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **grepping for a needle in a haystack**

This challenge involves understanding the use of the ```grep``` command in the command line. It is used when files to read are too big and we want to search for the occurence of a particular string in the file.

### Steps involved in approaching the challenge:

1. The challenge prompt clearly states that the ```/challenge/data.txt``` file needs to be read and it has a large amount of text, which is why the ```grep``` command will be used.
2. The clue that a flag always starts with the text ```pwn.college``` indicates that this is the string that needs to be searched for in the file.
3. Looking at the syntax of the use of the grep command to understand the command to be used for flag generation.
```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
4. ```SEARCH_STRING``` = ```pwn.college```
5. ```/path/to/file``` = ``` /challenge/data.txt```

### Flag Gengeration

* The following command is typed in the command line:
```
grep pwn.college /challenge/data.txt
```

* The following output is generated:
```
pwn.college{ATxLSl0shkXt7a6tUlPIaQtV8r9.ddTM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 5: **listing files**

The challenge deals with the use of the ```ls``` command to list the files present in a directory.

### Steps involved in approaching the challenge:

1. Following the prompt, the files present in the ```/challenge``` directory are listed using the following command:
```
ls /challenge
```
2. The following output is displayed:
```
29173-renamed-run-9527  DESCRIPTION.md

```
3. This gives us the name of the renamed ```run``` file, where the flag is present:
```
29173-renamed-run-9527
```

### Flag Generation:

* The following command is used to access the renamed file:
```
/challenge/29173-renamed-run-9527

```

* The following output is generated:
```
Yahaha, you found me! Here is your flag:
pwn.college{8fb7eyh1BLFL6aZvkT94kXHE53X.dhjM4QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 6: **touching files**

This challenge involves understanding the use of the ```touch``` command for the creation of a file.

### Steps involved in approaching the challenge:

1. According to the prompt, two files need to be created:
```/tmp/pwn``` and ```/tmp/college```
2. Thus the first step is to navigate into the ```tmp``` directory using the following command:
```
cd /tmp
```
3. The next step is to create the two files with the following commands:
```
touch pwn
touch college
```

### Flag Generation:

* After successfully creating the files, accoridng to the prompt, the following command is run for flag generation:
```
/challenge/run
```

* The following output is generated:
```
Success! Here is your flag:
pwn.college{Agb3yo6b639Pk6UjcFybhUQOi0p.dBzM4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 7: **removing files**

This challenge deals with understanding the use of the ```rm``` command to remove/delete files in a directory.

### Steps involved in approaching the challenge:
1. The current files present in the home directory are listed using the ```ls``` command.
The following output is generated:
```
Desktop  a  delete_me  leap
```
2. This confirms the presence of the ```delete_me``` file, which according to the prompt needs to be deleted.
3. Next, the file is removed using the following command:
```
rm delete_me
```
4. To check, the contents of the home directory are listed again using the ```ls``` command.
The following output is generated:
```
Desktop  a  leap
```
This confirms the deletion of the required file.

### Flag Generation:
* According to the prompt, the following command is run to access the flag:
```
/challenge/check
```
* The following output is generated:
```
Excellent removal. Here is your reward:
pwn.college{oRR2o6sZVx5dKi-3f3c1NJKA4Hn.dZTOwUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 8: **hidden files**

This challenge involves understanding how to access files that are prepended by ```.```, as the ```ls``` command does not display such files by default.
This involves the use of the ```-a``` operator with ```ls```.

### Steps involved in approaching the problem:

1. The prompt states that the flag is hidden as a dot prepended file in the ```/``` directory.
2. Thus it implies navigating into the ```/``` directory with the following command:
```
cd /
```
3. The next step involves listing all the files in the directory, including the ones prepended with ```.``` using the following command:
```
ls -a
```
The following output is generated:
```
.                     bin        etc    lib64   nix   run   tmp
..                    boot       home   libx32  opt   sbin  usr
.dockerenv            challenge  lib    media   proc  srv   var
.flag-29172305904359  dev        lib32  mnt     root  sys
```
4. Looking at all the files, the flag file is found:
```
.flag-29172305904359
```

### Flag generation:

* Having located the correct dot prepended file, the next step involves reading its contents using the ```cat``` command in order to access the flag:
```
cat .flag-29172305904359
```

* The following output is generated:
```
pwn.college{8RqMaN0ytjz4OnjLFkOaGyDGVsM.dBTN4QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 9: **An Epic Filesystem Quest**

This challenge involves a game to find a hidden flag using the ```cd```, ```ls``` and ```cat``` commands.

### Steps involved in approaching the challenge:
The following commands were run sequentially in response to the output produced at each step.

1. ```cd /```
2. ```ls```
3. ```cat TEASER```
4. ```cd /opt/aflplusplus/qemu_mode/qemuafl/authz```
5. ```ls```
6. ```cat TIP```
7. ```cd /usr/local/lib/python3.8/dist-packages/angr/analyses/decompiler/ccall_rewriters```
8. ```ls```
9. ```cat README```
10. ```cd /usr/lib/python3/dist-packages/sage/combinat/species```
11. ```ls```
12. ```cat MESSAGE```
13. ```ls /usr/share/emacs/26.3/etc/images/custom```
14. ```cat /usr/share/emacs/26.3/etc/images/custom/SPOILER-TRAPPED
15. ```cd /usr/lib/python3.9/lib2to3/pgen2```
16. ```ls -a```
17. ```cat .BLUEPRINT```
18. ```cd /usr/local/lib/python3.8/dist-packages/sympy/functions/special```
19. ```ls```
20. ```cat SECRET```
21. ```cd /usr/share/javascript/three/examples/jsm/animation```
22. ```ls```
23. ```cat MEMO```
24. ```cd /usr/share/lintian```

### Flag Generation:

* After performing the above series of commands, the final command that led to flag generation was:
```
cat DOSSIER
```
* Thus the flag was hidden in the ```/usr/share/lintian``` directory and had to be invoked using the above commands.
* On reading the ```DOSSIER``` file, the following output was generated:
```
cd /usr/share/lintian
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

