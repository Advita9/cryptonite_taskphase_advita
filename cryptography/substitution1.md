## substitution1

Challenge description:
```
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.
Download the message here.
```

Hints:
```
Try a frequency attack

Do the punctuation and the individual words help you make any substitutions?
```

Provided link:
```
https://artifacts.picoctf.net/c/183/message.txt
```
The message provided is:
```
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
```
Again we have a cryptogram (monoalphabetic substitution cipher), but no initial 26 letters.

We use a tool for frequency attack as given in the hints:
```
https://www.guballa.de/substitution-solver
```

On decrypting the message we get:
```
CTFs (short for capture the flag) are a type of computer security competition. Contestants are presented with a set of challenges which test their creativity, technical (and googling) skills, and problem-solving ability. Challenges usually cover a number of categories, and when solved, each yields a string (called a flag) which is submitted to an online scoring service. CTFs are a great way to learn a wide array of computer security skills in a safe, legal environment, and are hosted and played by many security groups around the world for fun and practice. For this problem, the flag is: picoCTF{FR3JU3NCY_4774CK5_4R3_C001_6E0659FB}

```

Thus the flag is:
```
picoCTF{FR3JU3NCY_4774CK5_4R3_C001_6E0659FB}
```
