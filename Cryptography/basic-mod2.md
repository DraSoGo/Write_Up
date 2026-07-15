```txt
104 372 110 436 262 173 354 393 351 297 241 86 262 359 256 441 124 154 165 165 219 288 42
```

Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.
หา mod inverse 41 แล้ว map ข้อมูลตามนี้
ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_

หา inverse ทุกตัว

![[Pasted image 20260710132317.png]]

28, 14, 22, 30, 18, 32, 30, 12, 25, 37, 8, 31, 18, 4, 37, 4, 1, 4, 1, 1, 3, 1, 1

map ข้อมูล

```python
abc = '0ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_'
cipher = [28, 14, 22, 30, 18, 32, 30, 12, 25, 37, 8, 31, 18, 4, 37, 4, 1, 4, 1, 1, 3, 1, 1]
for i in cipher:
    print(abc[i], end='')
```

1NV3R53LY_H4RD_DADAACAA
```
picoCTF{1NV3R53LY_H4RD_DADAACAA}
```