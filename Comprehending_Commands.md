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
