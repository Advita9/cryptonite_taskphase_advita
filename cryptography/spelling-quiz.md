## spelling-quiz

Challenge description:
```
I found the flag, but my brother wrote a program to encrypt all his text files. He has a spelling quiz study guide too, but I don't know if that helps.
```

directory provided:
```
https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/spelling-quiz/public.zip
```

On unzipping the directory, following files were found:
```
Archive:  public.zip
   creating: public/
  inflating: public/encrypt.py
  inflating: public/study-guide.txt
 extracting: public/flag.txt
```

encrypt.py:
```
import random
import os

files = [
    os.path.join(path, file)
    for path, dirs, files in os.walk('.')
    for file in files
    if file.split('.')[-1] == 'txt'
]

alphabet = list('abcdefghijklmnopqrstuvwxyz')
random.shuffle(shuffled := alphabet[:])
dictionary = dict(zip(alphabet, shuffled))

for filename in files:
    text = open(filename, 'r').read()
    encrypted = ''.join([
        dictionary[c]
        if c in dictionary else c
        for c in text
    ])
    open(filename, 'w').write(encrypted)
```

flag.txt:
```
brcfxba_vfr_mid_hosbrm_iprc_exa_hoav_vwcrm
```

study-guide.txt:
```
gocnfwnwtr
sxlyrxaic
dcrrtfrxcv
uxbvwavcq
lwvicwtiwm
pwtmwnxvicq
avingciisa
ylwtmrcawx
mwaxdcrrxuwlwvq
yciflwnf
mwaxsrtwvq
iovabxcabqwtd
bcrwtnlwtxvwit
srlxtwkwtd
bcriurmwrtv
nflicxlyicsxswmr
titrlrnvcilqvwn
xanrcvxwtxulr
vficxniblxavwra
bwttxnlrv
bxbrcerwdfva
wtnxctxvwit
titborcwlwvq
otbcrywtrm
ucxaalwgr
vcxtabiawvwpr
dlqnrcil
wmilxvcwkrc
fqbrcixcvwx
brcwsrmollxcq
crtmwvwit
sitavcwnwmr
rzvcxabrnvcxl
sitosrtvxllq
nfilrfrsxvwt
iprccrxlwas
mwttrclraa
nxcbrllos
uxccolrr
rzvciprcvrmtraa
trnraaxc
rpwtnwtd
brcabrnvwpwas
blxasilqkxuwlwvq
tinvwlonxl
wtvrcvxcaxl
raaiwtsrtv
bxcxvqbwn
uicavxll
swaxmcraawtd
xtvwvxurvwn
nisbovrcwkxulr
mrfwanra
crmimiwtd
biavtxaxl
swtxvicwxllq
nqllrtwxt
waocwmxr
axnnfxcwtr
nitprcaxkwitra
oterxcwaisr
vewtylierc
ulraawtd
otranxllibrm
xtnqliaviswxawa
kqsiaxta
miswtwjor
otfxuwvoxl
crwtnrtar
xovifrzxbliwm
monglwtdafwb
afwttrning
xlgrmxpq
xravwpxvr
blquixcm
otwabwnolxvr
anlrcivisq
rnnlrawilidwav
bcrgwtmrcdxcvrta
otbicnrlxwtwkrm
iprcnxllrm
wtxsicxvxa
xoziulxav
aocbxaawtdtraa
wtfxlxvic
afxcbwaf
brcmocxtv
```

looking at the contents of ```encrypt.py``` makes it obvious that this is the case of a substitution cipher. The ```subbreaker``` tool is downloaded and used:
```
pip install subbreaker
```

Based on the documentation, the following commands are provided:
```
subbreaker break --lang EN --ciphertext <(cat public/study-guide.txt | head -n 50)
```

Output:
```
Alphabet: abcdefghijklmnopqrstuvwxyz
Key:      xunmrydfwhglstibjcavopezqk
Fitness: 92.78
Nbr keys tried: 6175
Keys per second: 5290
Execution time (seconds): 1.167
Plaintext:
kurchicine
malfeasor
greenheart
baptistry
litorinoid
vindicatory
stockrooms
flindersia
disagreeability
frohlich
disamenity
outsparspying
preinclination
melanizing
preobedient
chloralformamide
nonelectrolytic
ascertainable
thoracoplasties
pinnaclet
paperweights
incarnation
nonpuerility
unprefined
brasslike
transpositive
glycerol
idolatrizer
hyperoartia
perimedullary
rendition
monstricide
extraspectral
monumentally
cholehematin
overrealism
dinnerless
carpellum
barrulee
extrovertedness
necessar
evincing
perspectivism
plasmolyzability
noctilucal
intertarsal
essoinment
paratypic
borstall
misadressing
```

Using the found key:
```
 subbreaker decode --key xunmrydfwhglstibjcavopezqk --ciphertext public/flag.txt
```

Output:
```
perhaps_the_dog_jumped_over_was_just_tired
```


Thus the flag obtained is:
```
picoCTF{perhaps_the_dog_jumped_over_was_just_tired}
```

