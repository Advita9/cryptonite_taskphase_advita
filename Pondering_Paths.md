# Pondering Paths

## Challenge 1: **The Root**
This challenge is to invoke the pwn directory using the command:
```
/pwn
```
### Understanding the command:
* `/` backslash placed before the name of the file/directory.
* `pwn` the program to invoke to grant access to the flag for this challenge.
* `/pwn` understanding the meaning of an *absolute path* - one that starts with the root directory.

### Flag Generation:
On running the command the following terminal output was displayed:
```
BOOM!!!
Here is your flag:
pwn.college{IQCTyZb871USXd1E6h4nsDOzsUi.dhzN5QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 2: **Program and absolute paths**
This challenge explores accessing a two-layer path. 
It involves accessing the ```/run``` directory placed inside the ```/challenge``` directory, which in turn lies inside root (concept of absolute path).

The command used to generate the flag:
```
/challenge/run
```

### Understanding the command:
* ```/challenge``` directory placed inside the root.
* ```/run``` the file with the challenge program. It needs to be accessed to get the flag. 
* ```/challenge/run``` is thus the absolute path of run.

### Flag Generation:
On running the command, the following terminal output was displayed:
```
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{Q6jBriMYwxaHKiv8cdz5MO5gJp0.dVDN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 3: **Position thy self**
This challenge deals with the correct use of the ```cd``` command on the command line.

### Steps involved in approaching the challenge:
1. Finding the correct working directory to cd into: Running the ```/challenge/run``` command gave the following output:

```
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
```

2. This was indication that the correct working directory is the ```/var``` directory.
3. The next step involved navigating to the ```/var``` directory using the following command:
```
cd /var
```

### Flag Generation:

* Once in the correct working directory, the following command was run to invoke the challenge:
```
/challenge/run
```
* The following output was generated:
```
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{USXMoqvnnQYypR13uiNnk-9IUrS.dZDN1QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 4: **Position elsewhere**
This challenge involves understanding the use of the ```cd``` command to **change** the correct working directory.

### Steps involved in approaching the challenge:
1. Finding the correct working directory to cd into: Running the ```/challenge/run``` command gave the following output:

```
Incorrect...
You are not currently in the /usr/share/doc directory.
Please use the `cd` utility to change directory appropriately.
```

2. This was indication that the correct working directory is the ```/usr/share/doc``` directory.
3. The next step involved navigating to the ```/usr/share/doc``` directory using the following command:

```
cd /usr/share/doc
```

### Flag Generation:

* Once in the correct working directory, the following command was run to invoke the challenge:
```
/challenge/run
```
* The following output was generated:
```
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{IcLZBO6t4w_mYTAqZKmyh-kshDo.ddDN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 5: Position yet elsewhere:

The challenge further deals with the use of the ```cd``` command to change the current working directory.

### Steps involved in approaching the challenge:
1. Finding the correct working directory to cd into: Running the ```/challenge/run``` command gave the following output:

```
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
```

2. This was indication that the correct working directory is the ```/var``` directory.
3. The next step involved navigating to the ```/var``` directory using the following command:
```
cd /var
```

### Flag Generation:

* Once in the correct working directory, the following command was run to invoke the challenge:
```
/challenge/run
```
* The following output was generated:
```
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{M-IaTnScqTuU6e0qn0tONBxfIvI.dhDN1QDL2MTO0czW}

```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

## Challenge 6: **implicit relative paths, from /**

This challenge deals with understanding **relative paths**, in contrast to absolute paths, which were being dealt with until now.

### Steps involved in approaching the challenge:
1. Tried accessing the challenge using the usual absolute path: ```/challenge/run``` and got the following output:
```
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
```
2. This implies using the ```cd /``` to navigate to the root directory.
3. Used the ```ls``` command to check the files under the ```/``` directory, and find the one starting with *c* following the hint in the prompt.
4. The ```challenge``` file should be the starting of the relative path we need to navigate into.

### Flag Generation:

* Once in the correct working directory, the following command was run to invoke the challenge:
```
challenge/run
```

* The following output was generated:
```
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8db8kFpv11WlNMUyyGTx6_HL8Kp.dlDN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


## Challenge 7: Explicit relative paths, from /

This challenge involves exploring more explicit relative paths. 

### Steps involved in approaching the challenge:
1. Tried the usual method to invoke the challenge using ```/challenge/run``` and got the following output:
```
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
```
2. This involves navigating to the ```/``` directory using the following command:
```
cd /
```

### Flag Generation:
* Using the challenge prompt hint of first navigating into ```/``` as the current working directory, and then using a relative path with ```.``` as part of it, the following command was run to invoke the challenge and get the flag:
```
./challenge/run
```

* The following output was generated:
```
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{MzMyiaHKmI7IpLBrkiVgs5jNBFh.dBTN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.


## Challenge 8: Implicit relative path
This challenge involves running paths using ```.``` from the ```/challenge``` directory, which is when Linux avoids looking in the current directory automatically (naked path provided).

### Steps involved in approaching the challenge:
1. As given in the challenge instructions, first navigated into the challenge directory using:
```
cd /challenge
```
2. The next step involves finding an appropriate relative path for ```run``` that explicitely signals Linux for invocation.

### Flag Generation:
* Using the challenge prompt hint of first navigating into ```/challenge``` as the current working directory, and then using a relative path with ```.``` as part of it, the following command was run to invoke the challenge and get the flag:
```
./run
```

* The following output was generated:
```
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8Fl9U0BQ7TVVoCIWK4xkYH8jaD3.dFTN1QDL2MTO0czW}
```
Hence the flag was procured, copied (first into the pwn terminal and then from the pwn clipboard to make it accessible to the system clipboard), and pasted into the pwn.college challenge page.

