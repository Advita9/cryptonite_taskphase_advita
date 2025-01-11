## rail-fence

Challenge description:
```
A type of transposition cipher is the rail fence cipher, which is described here. Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?
Download the message here.
Put the decoded message in the picoCTF flag format, picoCTF{decoded_message}.
```

Hints:
```
Once you've understood how the cipher works, it's best to draw it out yourself on paper
```

Message link provided:
```
https://artifacts.picoctf.net/c/188/message.txt
```

Based on the challenge description, it is a rail fence cipher, also known as zig zag cipher, a type of transposition cipher. The plaintext is written downwards diagonally on successive rails and moving up when the bottom rail is reached. The description states that the number of rails is 4.

Manual decryption is tried first by writing the letters in 4 lines. However, an online tool is finally used:
```
https://www.boxentriq.com/code-breaking/rail-fence-cipher
```

The result provided gives the flag:
```
The flag is: WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_4A76B997
```

So the final flag is:L
```
picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_4A76B997}
