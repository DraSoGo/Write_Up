
โจทย์ให้ disk img มา

```bash
gunzip timeline_0.img.gz
ls
timeline_0.img
```

เปิดใน Autopsy

![[Pasted image 20260713153941.png]]

จากโจทย์ชื่อ timeline ลองเช็ค timeline ดู

![[Pasted image 20260713154023.png]]

จะเห็นว่ามี Jan 1985 ที่แปลกๆเพราะเก่ามากๆ

![[Pasted image 20260713154105.png]]

ลองเช็คดูจะเจอไฟล์เดียวเลยลองเปิดไฟล์นั้นดู

![[Pasted image 20260713154158.png]]

เจอ base64 NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK

```bash
echo "NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK" | base64 -d
71m311n3_0u7113r_h3r_43a2e7af
```

```
picoCTF{71m311n3_0u7113r_h3r_43a2e7af}
```