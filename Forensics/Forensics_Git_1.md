mount และหา .git เหมือนเดิม

```bash
git log --oneline                                                                                                            
5fb8194 (HEAD -> master) Remove flag
177789a Add flag
```

177789a มี flag

```bash
git show 177789a
commit 177789af0b300e043ea8f54ea57d6cee352291ae
Author: ctf-player <ctf-player@example.com>
Date:   Wed Nov 19 09:20:05 2025 +0000

    Add flag

diff --git a/flag.txt b/flag.txt
new file mode 100644
index 0000000..f150f47
--- /dev/null
+++ b/flag.txt
@@ -0,0 +1 @@
+picoCTF{g17_r3m3mb3r5_d4ddf904}
\ No newline at end of file
```

```
picoCTF{g17_r3m3mb3r5_d4ddf904}
```