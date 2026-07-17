
ดูเหมือนว่าแฮกเกอร์จะอัปเกรด C2 (Command & Control) ที่ใช้ขโมยข้อมูลเป็นเวอร์ชันใหม่แล้ว
ไม่แน่ว่า… payload ที่ส่งออกมาอาจจะไม่ได้มาแบบธรรมดา ๆ เหมือนรอบที่แล้ว… XOR สักหน่อยดีไหม?

Flag format : flag{MD5}

![[Pasted image 20260717150952.png]]

สังเกตว่าตรง data มี hex อยู่ตรง len 63 ลอง dump ข้อมูลออกมา

```bash
tshark -r thctt2025_open_netsec2_upgraded-router.pcapng -Y "frame.len == 63" -T fields -e data.data | tr "\n" " "
```

```
51 5b 56 50 4c 52 06 51 56 0f 0e 55 55 0f 0e 55 01 00 0f 03 0f 53 07 56 0e 56 52 07 06 04 02 51 56 53 07 04 05 4a
```

เอาไปใส่ใน cyberchef

![[Pasted image 20260717151133.png]]

```
flag{e1fa89bb89b67848d0a9ae0135fad032}
```