โจทย์ให้ memdump กับ disk img มาผมลองแตกไฟล์ก่อน

```bash
gunzip memdump.mem.gz
```

ลอง strings แล้ว grep

```bash
strings memdump.mem | grep "picoCTF"
picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}
picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}
picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}
^C
```

```
picoCTF{B1tl0ck3r_dr1v3_d3crypt3d_9029ae5b}
```