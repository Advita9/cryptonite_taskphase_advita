## substitution0

Challenge description:
```
A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?
Download the message here.
```

Hints:
```
Try a frequency attack. An online tool might help.

```

Link provided:
```
https://artifacts.picoctf.net/c/153/message.txt
```

The message provided is:
```
OHNFUMWSVZLXEGCPTAJDYIRKQB 

Suauypcg Xuwaogf oacju, rvds o waoiu ogf jdoduxq ova, ogf hacywsd eu dsu huudxu
mace o wxojj noju vg rsvns vd roj ugnxcjuf. Vd roj o huoydvmyx jnoaohouyj, ogf, od
dsod dveu, yglgcrg dc godyaoxvjdj—cm ncyaju o wauod pavbu vg o jnvugdvmvn pcvgd
cm ivur. Dsuau ruau drc acygf hxonl jpcdj guoa cgu ukdauevdq cm dsu honl, ogf o
xcgw cgu guoa dsu cdsua. Dsu jnoxuj ruau uknuufvgwxq soaf ogf wxcjjq, rvds oxx dsu
oppuoaognu cm hyagvjsuf wcxf. Dsu ruvwsd cm dsu vgjund roj iuaq aueoalohxu, ogf,
dolvgw oxx dsvgwj vgdc ncgjvfuaodvcg, V ncyxf soafxq hxoeu Zypvdua mca svj cpvgvcg
aujpundvgw vd.

Dsu mxow vj: pvncNDM{5YH5717Y710G_3I0XY710G_03055505}
```

The first line of the message contains 26 letters, which hints that it is a mono-alphabetic substitution cipher. The following tool is used to decrypt, providing ```OHNFUMWSVZLXEGCPTAJDYIRKQB``` as the substitution alphabet:
```
https://www.dcode.fr/monoalphabetic-substitution?__r=1.fe0ef69f9cc66f378671564fc6d9592d
```

The flag is provided as output:
```
PICOCTF{5UB5717U710N_3V0LU710N_03055505}
```
