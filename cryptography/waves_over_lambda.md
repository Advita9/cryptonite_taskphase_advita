## waves over lambda

Challenge description:
```
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with nc jupiter.challenges.picoctf.org 43522.
```

Hints:
```
Flag is not in the usual flag format
```

After running the instance, we get the following:
```
jspwuhfy oeue ky istu qvhw - quedtepji_ky_j_saeu_vhrmgh_swqrhtpuhq
-------------------------------------------------------------------------------
be beue psf rtjo rsue fohp h dthufeu sq hp ostu stf sq stu yokx fkvv be yhb oeu ykpz, hpg foep k tpgeuyfssg qsu foe qkuyf fkre bohf bhy rehpf mi h yokx qstpgeukpw kp foe yeh.  k rtyf hjzpsbvegwe k ohg ohugvi eiey fs vssz tx boep foe yehrep fsvg re yoe bhy ykpzkpw; qsu qusr foe rsrepf fohf foei uhfoeu xtf re kpfs foe mshf fohp fohf k rkwof me yhkg fs ws kp, ri oehuf bhy, hy kf beue, gehg bkfokp re, xhufvi bkfo qukwof, xhufvi bkfo osuusu sq rkpg, hpg foe fostwofy sq bohf bhy ief meqsue re.
```

Based on the looks of it and previously solved crypto challenges, it looks like a monoalphabetic substitution cipher. We used the following tool to break the ciphertext:
```
https://www.guballa.de/substitution-solver
```

The output is:
```
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_ogfmaunraf
-------------------------------------------------------------------------------
we were not much more than a quarter of an hour out of our ship till we saw her sink, and then i understood for the first time what was meant by a ship foundering in the sea.  i must acknowledge i had hardly eyes to look up when the seamen told me she was sinking; for from the moment that they rather put me into the boat than that i might be said to go in, my heart was, as it were, dead within me, partly with fright, partly with horror of mind, and the thoughts of what was yet before me.

```


Thus the flag is:
```
frequency_is_c_over_lambda_ogfmaunraf
```

