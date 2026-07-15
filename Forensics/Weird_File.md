ได้ไฟล์ word มา

```bash
file weird_file.docm
weird_file.docm: Microsoft Word 2007+
```

hint ให้ดู [youtube]([https://www.youtube.com/watch?v=Y7IJjnLGqTQ](https://www.youtube.com/watch?v=Y7IJjnLGqTQ)) เวลา 5:47

![[Pasted image 20260713144517.png]]

```bash
olevba weird_file.docm
olevba 0.60.2 on Python 3.13.11 - http://decalage.info/python/oletools
===============================================================================
FILE: weird_file.docm
Type: OpenXML
WARNING  For now, VBA stomping cannot be detected for files in memory
-------------------------------------------------------------------------------
VBA MACRO ThisDocument.cls
in file: word/vbaProject.bin - OLE stream: 'VBA/ThisDocument'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Sub AutoOpen()
    MsgBox "Macros can run any program", 0, "Title"
    Signature

End Sub

 Sub Signature()
    Selection.TypeText Text:="some text"
    Selection.TypeParagraph

 End Sub

 Sub runpython()

Dim Ret_Val
Args = """" '"""
Ret_Val = Shell("python -c 'print(\"cGljb0NURnttNGNyMHNfcl9kNG5nM3IwdXN9\")'" & " " & Args, vbNormalFocus)
If Ret_Val = 0 Then
   MsgBox "Couldn't run python script!", vbOKOnly
End If
End Sub
+----------+--------------------+---------------------------------------------+
|Type      |Keyword             |Description                                  |
+----------+--------------------+---------------------------------------------+
|AutoExec  |AutoOpen            |Runs when the Word document is opened        |
|Suspicious|Shell               |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|vbNormalFocus       |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|run                 |May run an executable file or a system       |
|          |                    |command                                      |
+----------+--------------------+---------------------------------------------+
```

ได้ base64 มา cGljb0NURnttNGNyMHNfcl9kNG5nM3IwdXN9

```bash
echo "cGljb0NURnttNGNyMHNfcl9kNG5nM3IwdXN9" | base64 -d
picoCTF{m4cr0s_r_d4ng3r0us}
```

```
picoCTF{m4cr0s_r_d4ng3r0us}
```
