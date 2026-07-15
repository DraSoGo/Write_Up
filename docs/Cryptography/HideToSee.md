![[Pasted image 20260710153617.png]]

ได้ภาพนี้มาเช็ค steghide
```bash
steghide info HideToSee.jpg
"HideToSee.jpg":
  format: jpeg
  capacity: 2.4 KB
Try to get information about embedded data ? (y/n) y
Enter passphrase:
  embedded file "encrypted.txt":
    size: 31.0 Byte
    encrypted: rijndael-128, cbc
    compressed: yes
```

มี encrypted.txt อยู่

```bash
steghide extract -sf HideToSee.jpg
Enter passphrase:
wrote extracted data to "encrypted.txt".
```

ใน encrypted.txt

```txt
krxlXGU{zgyzhs_xizxp_92533667}
```

จากภาพตอนแรกน่าจะเป็น Atbash Cipher

![[Pasted image 20260710153832.png]]

```
picoCTF{atbash_crack_92533667}
```