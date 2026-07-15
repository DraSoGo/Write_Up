![[Pasted image 20260713142035.png]]


ค้นพนธงที่น่าสนใจคืออันนี้ Upanzi, Republic The

![[Pasted image 20260713142107.png]]

ผมเลยโหลภาพมา

```bash
zsteg flags_are_stepic.png
/home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:369:in `prev_scanline_byte': stack level too deep (SystemStackError)
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:304:in `block in decoded_bytes'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:303:in `upto'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:303:in `decoded_bytes'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:304:in `block in decoded_bytes'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:303:in `upto'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zpng-0.4.6/lib/zpng/scan_line.rb:303:in `decoded_bytes'
	 ... 10225 levels...
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zsteg-0.2.14/lib/zsteg.rb:26:in `run'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/gems/zsteg-0.2.14/bin/zsteg:8:in `<top (required)>'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/bin/zsteg:25:in `load'
	from /home/drasogo/.local/share/gem/ruby/3.3.0/bin/zsteg:25:in `<main>'
```

จะเห็นว่าภาพต้อง decode จากโจทย์ใบ้ stepic

```python
from PIL import Image
import stepic
img = Image.open("flags_are_stepic.png")
txt = stepic.decode(img)
print(txt)
```

```
picoCTF{fl4g_h45_fl4g03264f88}
```