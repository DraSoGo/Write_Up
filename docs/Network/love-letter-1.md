โจทย์ให้ pcap มา follow tcp ไปจะเจอแบบนี้

![[Pasted image 20260717185747.png]]

ผมเลยเอาแต่ละ part มาต่อกันเป็น txt file

![[Pasted image 20260717185824.png]]

love.txt ลองเอาไป decode base64

![[Pasted image 20260717185923.png]]

มันเหมือนโครงสร้างไฟล์ผมเลยลองแปลงเป็น hex

![[Pasted image 20260717185952.png]]

นำ hex ไปเช็คกับ file signatures พบว่าตรงกับ zip file (50 4b 03 04)

![[Pasted image 20260717190036.png]]

เลยเป็น love.txt เป็นไฟล์ zip

```bash
cat love.txt | base64 -d > love.zip
```

unzip file

```bash
unzip love.zip
Archive:  love.zip
  inflating: love_letter.txt
```

อ่านไฟล์

```bash
cat love_letter.txt
```

```
My dearest,

I built a special chair for us inside our Minecraft world. Each block holds a piece of my heart. Every pixel of wood is carved with a memory of our adventures.

Hidden within this world lies a message meant only for you. To uncover it, you'll need to open the chair and piece together the bytes I left. When you find the secret, you'll have proof of how much you mean to me.

As always, our love is encoded not in commands, but in the time we spend decoding the world we build.

Love always,
Your secret admirer

flag{f0b3e7e3568616fa6d4a22ad0ed4c89e}
```

```
flag{f0b3e7e3568616fa6d4a22ad0ed4c89e}
```