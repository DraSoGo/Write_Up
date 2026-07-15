ได้ pcap มา

![[Pasted image 20260715195432.png]]

ดูไปเรื่อยๆ

![[Pasted image 20260715195455.png]]

เจอ nothing sus ซึ่งโครต sus เลย filter http ดู

![[Pasted image 20260715195635.png]]

เจอ 2 ภาพส่งไปยัง powershell.org

dump ภาพออกมา

![[Pasted image 20260715195745.png]]

evil_duck น่าสนใจ คิดว่าต้องเป็นการเอา duck มา Steganography ไปเป็น evil duck ลองใช้ zsteg กับ steghide ไม่เจออะไร คิดว่าเป็น Steganography แบบอื่นเลย search หาเกี่ยวกับ powershell Steganography ดู


![[Pasted image 20260715200138.png]]

![[Pasted image 20260715200157.png]]

![[Pasted image 20260715200210.png]]

ได้ tool แล้วเป็น .exe เลยเอาไป run vm window

![[Pasted image 20260715200243.png]]
![[Pasted image 20260715200259.png]]
ได้แบบนี้มา

```pwsh
$out = "flag.txt"
$enc = [system.Text.Encoding]::UTF8
$string1 = "HEYWherE(IS_tNE)50uP?^DId_YOu(]E@t*mY_3RD()B2g3l?"
$string2 = "8,:8+14>Fx0l+$*KjVD>[o*.;+1|*[n&2G^201l&,Mv+_'T_B"

$data1 = $enc.GetBytes($string1)
$bytes = $enc.GetBytes($string2)

for($i=0; $i -lt $bytes.count ; $i++)
{
    $bytes[$i] = $bytes[$i] -bxor $data1[$i]
}
[System.IO.File]::WriteAllBytes("$out", $bytes)
```

run script powershell ใน kali

![[Pasted image 20260715200414.png]]

```bash
cat flag.txt
picoCTF{n1c3_job_f1nd1ng_th3_s3cr3t_in_the_im@g3}
```

```
picoCTF{n1c3_job_f1nd1ng_th3_s3cr3t_in_the_im@g3}
```