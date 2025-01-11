## caesar

Challenge description:
```
Decrypt this message.
```

Hints:
```
caesar cipher tutorial: https://privacycanada.net/classical-encryption/caesar-cipher/
```

Message link:
```
https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext
```

The provided message is:
```
picoCTF{ynkooejcpdanqxeykjrbdofgkq}
```
Based on the articel, Caesar cipher is a shift cipher/ substitution cipher where each letter i the original message is replaced with a letter corresponding to a certain number of letters shifted up or down in the alphabet. 

```
ynkooejcpdanqxeykjrbdofgkq
```
 is placed in an online Caesar decryption tool:
```
https://cryptii.com/pipes/caesar-cipher
```

Shifts are made until something slightly meaningful is found. Finally at 22 shifts, we get:
```
crossingtherubiconvfhsjkou
```

Thus the flag is:
```
picoCTF{crossingtherubiconvfhsjkou}
```

