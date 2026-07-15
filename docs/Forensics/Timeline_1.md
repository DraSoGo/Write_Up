โจทย์ให้ disk img มา
เช็ค timeline เหมือนเดิม

![[Pasted image 20260713161948.png]]

โจทย์ใบ้มาว่าเป็นเวลาใหม่สุดเลยเช็ค Dec 2025

![[Pasted image 20260713162040.png]]

ไฟล์เยอะมากคำใบ้ให้เช็คแค่ macb

เราจึงควร dump ข้อมูลออกมาเพื่อ grep

```bash
tsk_gettimes timeline_1 > timeline_1.txt

mactime -b timeline_1.txt > timeline_1.csv
Old package separator "'" deprecated at /usr/bin/mactime line 154.
Old package separator "'" deprecated at /usr/bin/mactime line 167.
```

เนื่องจากเป็นเวลาใหม่สุดเลยเช็คจาก tail

```bash
tail timeline_1.csv -n 100 | grep "macb"
                                3 macb l/lrwxrwxrwx 0        0        67318    usr/bin/rview -> vim
                                3 macb l/lrwxrwxrwx 0        0        67319    usr/bin/rvim -> vim
                                3 macb l/lrwxrwxrwx 0        0        67320    usr/bin/view -> vim
                               49 macb r/rrw-r--r-- 0        0        32716    etc/chat
                             1024 macb d/drwxr-xr-x 0        0        33017    lib/rc/cache
                                8 macb r/rrw-r--r-- 0        0        33020    lib/rc/cache/softlevel
                                9 macb r/rrw------- 0        0        4943     root/.ash_history
                               32 macb r/rr-------- 0        0        65278    var/lib/seedrng/seed.credit
```

ลองเปิด etc/chat ดู

![[Pasted image 20260713162451.png]]

ได้ base64 NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK

```bash
echo "NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK" | base64 -d
573417h13r_7h4n_7h3_1457_58527bb222
```

```
picoCTF{573417h13r_7h4n_7h3_1457_58527bb222}
```