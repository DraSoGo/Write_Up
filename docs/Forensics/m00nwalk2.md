โจทย์ให้ไฟล์เสียงมา 4 อันคือ message clu1 clu2 clu3

ใช้ sstv decode

```bash
sstv -d message.wav -o message.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...                          [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

![[message.png]]

flag เก่าไม่ใช่ flag จริง

```bash
sstv -d clue1.wav -o clue1.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Martin 1
[sstv] Decoding image...                          [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

![[clue1.png]]

```bash
sstv -d clue2.wav -o clue2.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 2
[sstv] Decoding image...                          [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

![[clue2.png]]

```bash
sstv -d clue3.wav -o clue3.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Martin 2
[sstv] Decoding image...                          [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

![[clue3.png]]

ได้มาว่าเป็น Steganography ที่มี password เป็น hidden_stegosaurus

ลองเช็คใน message.wav

```bash
steghide info message.wav
"message.wav":
  format: wave audio, PCM encoding
  capacity: 337.7 KB
Try to get information about embedded data ? (y/n) y
Enter passphrase:hidden_stegosaurus
  embedded file "steganopayload12154.txt":
    size: 46.0 Byte
    encrypted: rijndael-128, cbc
    compressed: yes
```

เจอ steganopayload12154.txt ลอง extract ออกมา

```bash
steghide extract -sf message.wav
Enter passphrase:hidden_stegosaurus
wrote extracted data to "steganopayload12154.txt".
```

```bash
cat steganopayload12154.txt
picoCTF{the_answer_lies_hidden_in_plain_sight}
```

```
picoCTF{the_answer_lies_hidden_in_plain_sight}
```