![[Pasted image 20260708185236.png]]

PLMN=00101 CELLID=90461

CELLID=90461
![[Pasted image 20260708185352.png]]

IMSI:310410337059687

Export HTTP
![[Pasted image 20260708185431.png]]

```bash
ls
 rogue_tower.pcap   upload  'upload(1)'  'upload(2)'  'upload(3)'  'upload(4)'	'upload(5)'
```

```bash
cat upload upload\(1\) upload\(2\) upload\(3\) upload\(4\) upload\(5\)
Q15TWnpifkxBB1dACmlbBF9bb0EJQQtFbAQBBQ1QXAEASg==
```

![[Pasted image 20260708190144.png]]

น่าจะต้อง xor สักอย่างนึง
IMSI:310410337059687
![[Pasted image 20260708190418.png]]
ยังไม่ใช่
![[Pasted image 20260708190253.png]]
สังเกตว่าทุก http จะมี IMSI เหมือนกันคือส่วน 310410 ด้านหลังจะต่างกันผมเลยลอง 337059687
![[Pasted image 20260708190402.png]]
ผมเลยลองลบตัวข้างหน้า 1 ตัว 37059687
![[Pasted image 20260708190504.png]]

```
picoCTF{r0gu3_c3ll_t0w3r_3104fd63}
```