A crash dump from an analyst workstation was captured before the system was wiped. Plain strings only show fragments, and the interesting buffer never appears in one piece. Use the memory snapshot and the process map to reconstruct the resident data, then undo the page-level transform to recover the flag.
ได้มา 2 ไฟล์

process_map.txt

```
Process map from the crash collector:

pid  name               base      size    xor tag
111  systemd            0x7f1000  0x1200  tag=STEDY
482  explorer           0x7f4000  0x2400  tag=CLIP9
901  photo_recover      0x8a0000  0x3c00  tag=DR1FT
1044 crash_handler      0x900000  0x1800  tag=PGOFF

Each process scrambled its resident buffer with its own tag (a repeating XOR key).
The buffer of interest was mapped across three pages before the dump was written;
identify which process owns those pages, then apply its tag across the whole buffer.
```

ram_dump.txt

```
Memory capture excerpt (page-aligned)
=====================================

PAGE 0x8a0000
00000000  25 26 59 23 3a 25 29 43 27 39 1b 22              |%&Y#:%)C'9."|
00000010  1f 19 1c 0a de ad be ef 08 0f 1c 1a 0a 3d 0d 0d  |.............=..|

PAGE 0x8a1000
00000000  50 21 31 37 0d 59 2f 30 21 0d 57 34              |P!17.Y/0!.W4|
00000010  11 0c 17 05 fa ce b0 0c 11 0c 17 05 07 13 0a 0b  |................|

PAGE 0x8a2000
00000000  35 23 3f 54 28 20 37 2f                          |5#?T( 7/|
00000010  0c 1a 05 07 0c 0e 07 0f 06 1d 10 12 0a 0b 0d 1f  |................|

captured note: the buffer was XORed before the pages were dumped.

```

photo_recover น่าจะเป็น flag มี 32 byte เอา 00000000 ของทุก page มาต่อกันได้ 32 byte พอดี

25 26 59 23 3a 25 29 43 27 39 1b 22 50 21 31 37 0d 59 2f 30 21 0d 57 34 35 23 3f 54 28 20 37 2f

decode hex ดู

![[Pasted image 20260719141501.png]]

ยังไม่ได้น่าจะต้อง xor ลอง xor ด้วย format flag

![[Pasted image 20260719141605.png]]

DR1FTDR ได้แบบนี้จะสังเกตว่าเป็น xor loop (DR1FT   DR) โดย key คือ DR1FT

![[Pasted image 20260719141712.png]]

```
athena{ram_pages_hide_fragments}
```