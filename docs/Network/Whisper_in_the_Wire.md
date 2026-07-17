ฐานทัพไซเบอร์แห่งใหม่เพิ่งถูกสร้างขึ้นโดยประเทศเพื่อนบ้าน พวกเขาใช้ระบบควบคุมแบบ gRPC over HTTP/2 เพื่อซ่อนคำสั่งลับและข้อมูลสำคัญระหว่าง นักวิจัยและเซิร์ฟเวอร์ทดสอบอาวุธ แต่โชคดี ที่หน่วยไซเบอร์ของเราได้ แอบเก็บ ไฟล์ PCAP ที่บันทึกการสื่อสารได้มาแล้ว 🎧 แรก ๆ มันดูเหมือนข้อมูลไร้ค่า ที่อ่านไม่ออกทันที, ข้อความยังดูเหมือนอาจจะถูกบีบอัดด้วย zlib ไว้ อีกต่างหาก… อย่างไรก็ตาม มีข่าวลือว่า ข้อความตอบกลับจาก ซ่อน flag เอาไว้! 🏴☠️ ภารกิจของคุณคือแกะรอยจากไฟล์ PCAP เพื่อดึง flag ที่ถูกซ่อนอยู่ให้ได้

Flag format : flag{MD5}

ได้ pcap มา

![[Pasted image 20260717152009.png]]

ลองดู http

![[Pasted image 20260717152044.png]]

เหมือนจะมีไฟล์น่าสนใจ

![[Pasted image 20260717152112.png]]

แต่ export ไม่เจอ

ผมเลยลอง binwalk ดู

```bash
binwalk -e thctt2025_open_netsec3_whisper-in-the-wire.pcapng

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
16821         0x41B5          Zlib compressed data, default compression
21113         0x5279          Zlib compressed data, default compression
```

```bash
cd _thctt2025_open_netsec3_whisper-in-the-wire.pcapng.extracted
ls
41B5  41B5.zlib  5279  5279.zlib
```

```bash
cat 41B5
nope
```

```bash
cat 5279
flag{fd3ca5a5acce56f112a725ce433c96e4}
```

```
flag{fd3ca5a5acce56f112a725ce433c96e4}
```