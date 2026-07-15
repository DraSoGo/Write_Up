mount และหา .git เหมือนเดิม

```bash
git log --oneline                                                                                                                    
fatal: your current branch 'master' does not have any commits yet
```

ไม่เจอ log ผมเลยไปหาในไฟล์เลย

```bash
cd .git/logs
ls
HEAD  refs

strings HEAD                                                                    
0000000000000000000000000000000000000000 2c0a9b2b15dce92f800393d5030c7454efc278ae ctf-player <ctf-player@example.com> 1763549240 +0000	commit (initial): Add netcat scripts
2c0a9b2b15dce92f800393d5030c7454efc278ae 26b809e0c41d8421f1126ed3a4eb06ad66e6d90a ctf-player <ctf-player@example.com> 1763549240 +0000	commit: Add video game chat log
26b809e0c41d8421f1126ed3a4eb06ad66e6d90a 5827632e046a80a1e0d7b4fc5c7800dd539baeaf ctf-player <ctf-player@example.com> 1763549240 +0000	commit: Add TV show chat log
5827632e046a80a1e0d7b4fc5c7800dd539baeaf e80b38b3322a5ba32ac07076ef5eeb4a59449875 ctf-player <ctf-player@example.com> 1763549240 +0000	commit: Add secret hideout chat log
e80b38b3322a5ba32ac07076ef5eeb4a59449875 2151ef0ccc15aed1ab88e1afdc7484aaeff211c4 ctf-player <ctf-player@example.com> 1763549240 +0000	commit: Remove secret hideout log
2151ef0ccc15aed1ab88e1afdc7484aaeff211c4 01533f718556a0e59f1467dae4fa462eed82c2a1 ctf-player <ctf-player@example.com> 1763549240 +0000	commit: Add random chat log
```

e80b38b3322a5ba32ac07076ef5eeb4a59449875 น่าจะมี flag

```bash
it show e80b38b3322a5ba32ac07076ef5eeb4a59449875
commit e80b38b3322a5ba32ac07076ef5eeb4a59449875
Author: ctf-player <ctf-player@example.com>
Date:   Wed Nov 19 10:47:20 2025 +0000

    Add secret hideout chat log

diff --git a/logs/3.txt b/logs/3.txt
new file mode 100644
index 0000000..7178644
--- /dev/null
+++ b/logs/3.txt
@@ -0,0 +1,3 @@
+Rex: Meet at the old arcade basement for the secret hideout.
+Jay: Ask Rusty at the door and use password picoCTF{g17_r35cu3_16ac6bf3}.
+Rex: Bring the decoder map so we can plan the route.
```

```
picoCTF{g17_r35cu3_16ac6bf3}
```