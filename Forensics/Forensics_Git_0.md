ได้ disk img มาแต่ข้อนี้เป็น git เลยไม่ได้ใช้ autopsy เพราะต้องรัน git ใน cmd

![[Pasted image 20260713174355.png]]

Mounter img

![[Pasted image 20260713174425.png]]

เปิด img หา .git

![[Pasted image 20260713174444.png]]

เข้ามาใน folder ที่มี .git

![[Pasted image 20260713174520.png]]

run terminal

```bash
git config --global --add safe.directory /run/media/drasogo/7a00e9da-98f8-4f0f-b257-95edf422d902/home/ctf-player/Code/secrets

git log                                                                                                                      
commit 327681bb38cf467cec328eec9707b240e3e74ced (HEAD -> master)
Author: ctf-player <ctf-player@example.com>
Date:   Wed Nov 19 08:49:27 2025 +0000

    Wrap this phrase in the flag format: g17_1n_7h3_d15k_041217d8
```

```
picoCTF{g17_1n_7h3_d15k_041217d8}
```