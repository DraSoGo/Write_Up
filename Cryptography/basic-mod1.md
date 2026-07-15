
```txt
350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213 
```

Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.
เอาค่าไป mod 37 แล้ว map ตามนี้
ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_

```python
abc = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_'
cipher = [350,63,353,198,114,369,346,184,202,322,94,235,114,110,185,188,225,212,366,374,261,213]
for i in cipher:
    print(abc[i % len(abc)], end='')
```

R0UND_N_R0UND_ADD17EC2
```
picoCTF{R0UND_N_R0UND_ADD17EC2}
```