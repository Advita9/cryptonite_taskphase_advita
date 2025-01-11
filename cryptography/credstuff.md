## credstuff

Challenge description:
```
We found a leak of a blackmarket website's login credentials. Can you find the password of the user cultiris and successfully decrypt it?
Download the leak here.
The first user in usernames.txt corresponds to the first password in passwords.txt. The second user corresponds to the second password, and so on.
```
Hints:
```
Maybe other passwords will have hints about the leak?
```

Leak link provided:
```
https://artifacts.picoctf.net/c/151/leak.tar
```

The file is decrypted:
```
tar -xvf leak.tar
```

Output:
```
leak/
leak/passwords.txt
leak/usernames.txt
```

We enter into the leak directory and then find the line number of user ```cultiris``` in the ```usernames.txt``` file:
```
cat usernames.txt | grep -ni "cultiris"
```

Output:
```
378:cultiris
```

We lookup line 378 in the ```passwords.txt``` file and get:
```
cvpbPGS{P7e1S_54I35_71Z3}
```


This is put into a ROT13 decoder and we get the flag:
```
picoCTF{C7r1F_54V35_71M3}
```

