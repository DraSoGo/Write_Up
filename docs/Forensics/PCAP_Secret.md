Incident response pulled a tiny packet capture from a suspect jump host—`forensic_pcap_secret.pcap.gg`. Most of the traffic looks like routine DNS and HTTP noise, but analysts swear one of these connections is exfiltrating the flag to an external host. Download the capture, find the suspicious connection, and recover the hidden flag.

ได้ forensic_pcap_secret.pcap.gg

```bash
binwalk -e forensic_pcap_secret.pcap.gg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             gzip compressed data, maximum compression, has original file name: "forensic_pcap_secret.pcap", last modified: 1970-01-01 00:00:00 (null date)
```

ได้ pcap มา

![[Pasted image 20260719140925.png]]

follow tcp ไปเจอนี่

![[Pasted image 20260719140954.png]]

decode base64

```bash
echo "YXRoZW5he3BjNHBfaDFkMzVfMW5fdzFyM30=" | base64 -d
athena{pc4p_h1d35_1n_w1r3}
```

```
athena{pc4p_h1d35_1n_w1r3}
```