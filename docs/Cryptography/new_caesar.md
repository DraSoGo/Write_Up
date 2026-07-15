```python
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
	enc = ""
	for c in plain:
		binary = "{0:08b}".format(ord(c))
		enc += ALPHABET[int(binary[:4], 2)]
		enc += ALPHABET[int(binary[4:], 2)]
	return enc

def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
	enc += shift(c, key[i % len(key)])
print(enc)
```

break code แล้วสร้าง code decryption brute force 1 ตัวอักษรจาก `assert len(key) == 1`

```python
import string
cipher = "fegdeogdgecoeocgcgchcfcffccfca"
LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]

def b16_decode(b16):
	dec = ""
	for i in range(0, len(b16), 2):
		binary = "{0:04b}{1:04b}".format(ALPHABET.index(b16[i]), ALPHABET.index(b16[i+1]))
		dec += chr(int(binary, 2))
	return dec

for key in ALPHABET:
    flag = ""
    print(f"Key: {key}")
    for char in cipher:
        flag += shift(char, key)
    print(b16_decode(flag))
```

```
Key: a
TcNcd.N&&'%%R%
Key: b
et_tu?_77866c61
Key: c
v`@`HHIGGtGB
Key: d
qQqYYZXXXS
Key: e
§§¨bjjkiiid
Key: f
©¸¸¹s{{|zz§zu
Key: g
ºÉ¤ÉÊ¤¸
Key: h
ËÚµÚÛµÉ
Key: i
ÜëÆëì¦Æ®®¯­­Ú­¨
Key: j
íü×üý·×¿¿°¾¾ë¾¹
Key: k
ÈèÀÀÁÏÏüÏÊ
Key: l
ÐÛùÑÑÒÐÐ
Key: m
/
/ ê
ââãáááì
Key: n
!01û
ey: o
2A,AB
     ,0
Key: p
CR=RS=A
```

ข้อความที่ดูเป็น flag ได้คือ Key: b

```
picoCTF{et_tu?_77866c61}
```