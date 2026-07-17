ได้ pcap มา

![[Pasted image 20260717190747.png]]

ดูใน tcp

![[Pasted image 20260717190904.png]]

รวมทุก part จะได้แบบนี้

```
2504020b004d071c0e0a0305426d65210e00002c
0c154e0e1c4d090b150a436b2747070c170b4707
04050a02014d0000081b05041c470208121d0608
084108081d4d180112414d6b6401030c0615525f
0b030f5f595d0258045a5e555d510c0f0008010a
55525756595c580b5158106b
```

เป็น hex แน่ๆ ลอง decode ดู

![[Pasted image 20260717191010.png]]

ยังไม่ได้
ลองดูใน udp

![[Pasted image 20260717190817.png]]

เราจะเจอ xor key คือ mango
ลองใส่ xor หลัง decode hex ดู

![[Pasted image 20260717191102.png]]

```
flag{50fba860c6c53436cbaffe8391619e67}
```