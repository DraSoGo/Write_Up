```txt
heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V6E5926A}4
```

เราจะสังเกตได้ว่าข้อความจริงต้องเป็น The flag...
ซึ่งมันสามารถอ่านได้ด้วยการแบ่งเป็น block ละ 3 ตัวอักษร แล้วเอาตัวหลังสุดมาไว้นด้านหน้าสุด เช่น
heT -> The
fl- -> -fl
g-a -> ag-
แทนที่ " " ด้วย "-" เพื่อให้เห็นภาพ

เอามารวมกันได้ The-flag-

```python
cipher = "heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V6E5926A}4"
A = []
for i in range(0, len(cipher), 3):
    c = ""
    for j in range(3):
        c += cipher[i + j]
    A.append(c)
for i in A:
    print(f"{i[2]}{i[0]}{i[1]}", end="")
```

The flag is picoCTF{7R4N5P051N6_15_3XP3N51V3_56E6924A}

```
picoCTF{7R4N5P051N6_15_3XP3N51V3_56E6924A}
```
