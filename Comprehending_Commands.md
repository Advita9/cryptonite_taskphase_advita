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

* Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.
