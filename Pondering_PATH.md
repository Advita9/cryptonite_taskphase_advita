# Pondering PATH

## Challenge 1: **The PATH Variable**
This challenge involves understanding how to edit ```PATH``` to remove the existence of certain commands.

### Steps involved in approaching the challenge:
1. The prompt states that the ```/challenge/run``` program will delete the flag if it is able to find the ```rm``` command.
2. Thus, first the PATH is erased using:
```
PATH=""
```
### Flag Generation:
* The following command is used to generate the flag:
```
/challenge/run
```
It should not be able to find the ```rm``` command
* The following output is generated:
```
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{M4d_-2hPDH5MKsjj8rIqVWtFpC5.dZzNwUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

```

## Challenge 2: **Setting PATH**
This challenge involves understanding how tomaintain useful scripts that can be launched only by name, by adding it to PATH.

### Steps involved in approaching the challenge:
1. The prompt states that the ```win``` command exists in the ```/challenge/more_commands/``` directory, and is the only thing ```/challenge/run``` needs.
2. The PATH is set using:
```
PATH=/challenge/more_commands/
```

### Flag Generation:
* Once the PATH is set properly, the ```win``` command can be invoked by ```/challenge/run``` using:
```
/challenge/run
```
* The following output is generated:
```
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{0y_vAxOSsgggE8MneHCRkxBZ8EX.dVzNyUDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


