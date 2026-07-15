![[Pasted image 20260708184520.png]]

```bash
tshark -r dump.pcap -Y 'eth' -T fields -e data | xxd -r -p

rnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagrnet secret: Is this the flagould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?ould the flag have been splitted?VGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=bababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSbababkjaASKBKSBACVVAVSDDSSSSDSKJBJSaybe try checking the other fileaybe try checking the other fileaybe try checking the other fileaybe try checking the other fileaybe try checking the other fileaybe try checking the other fileaybe try checking the other fileaybe try checking the other file
```

```bash
echo "VGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=" | base64 -d
This is the secret: picoCTF{R34DING_LOKd_
```

```bash
unzip -P "picoCTF{R34DING_LOKd_" flag.zip
Archive:  flag.zip
 extracting: flag
```

```bash
cat flag
picoCTF{R34DING_LOKd_fil56_succ3ss_494c4f32}
```
