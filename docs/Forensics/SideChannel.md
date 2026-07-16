โจทย์ให้ไฟล์โปรแกรมมาลองรันดู

```bash
chmod +x SideChanneld
./SideChannel
Please enter your 8-digit PIN code:
12345678
8
Checking PIN...
Access denied
```

เป็นการใส่ pin 8 ตัวให้ถูก

โจทย์ใบ้ว่าเกี่ยวกับ "timing-based side-channel attacks."

![[Pasted image 20260716144907.png]]

ถ้าเราพิจารณาดีๆจะเห็นว่าถ้าเราเดารหัสทีละตัวแล้วรหัสนั้นจะถูกก็ต่อเมื่อรหัสนั้นใช้เวลาตรวจนานที่สุด ผมเลยเขียน python เพื่อไล่หาตัวเลขทุกหลักที่ใช้เวลานานสุด

```python
import time
import subprocess
def run_sidechannel(pin):
    start = time.time()
    result = subprocess.run(["./SideChannel"], input=pin.encode(), capture_output=True)
    end = time.time()
    return end - start

pin = ""

for i in range(8):
    best = ""
    mx_time = 0
    for d in "0123456789":
        tmp = pin + d + "0"*(7-i)
        time_n = run_sidechannel(tmp)
        if time_n > mx_time:
            mx_time = time_n
            best = d
    print(best)
    pin += best
    print(pin)
```

```bash
python sidechannel.py
4
4
8
48
3
483
9
4839
0
48390
5
483905
1
4839051
3
48390513
```

แสดงว่า pin คือ 48390513

```bash
nc saturn.picoctf.net 54930
Verifying that you are a human...
Please enter the master PIN code:
48390513
Password correct. Here's your flag:
picoCTF{t1m1ng_4tt4ck_9803bd25}
```

```
picoCTF{t1m1ng_4tt4ck_9803bd25}
```