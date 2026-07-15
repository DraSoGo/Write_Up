สิ่งที่โจทย์ให้มา
source

```python
from Crypto.Cipher import AES
import hashlib
import random

# /usr/share/dict/words from
# https://gist.githubusercontent.com/wchargin/8927565/raw/d9783627c731268fb2935a731a618aa8e95cf465/words
with open("/usr/share/dict/words") as f:
    words = [w.strip() for w in f.readlines()]
keyword = random.choice(words)

KEY = hashlib.md5(keyword.encode()).digest()
FLAG = ?


@chal.route('/passwords_as_keys/decrypt/<ciphertext>/<password_hash>/')
def decrypt(ciphertext, password_hash):
    ciphertext = bytes.fromhex(ciphertext)
    key = bytes.fromhex(password_hash)

    cipher = AES.new(key, AES.MODE_ECB)
    try:
        decrypted = cipher.decrypt(ciphertext)
    except ValueError as e:
        return {"error": str(e)}

    return {"plaintext": decrypted.hex()}


@chal.route('/passwords_as_keys/encrypt_flag/')
def encrypt_flag():
    cipher = AES.new(KEY, AES.MODE_ECB)
    encrypted = cipher.encrypt(FLAG.encode())

    return {"ciphertext": encrypted.hex()}
```

cipher text = c92b7734070205bdf6c0087a751466ec13ae15e6f1bcdd3f3a535ec0f4bbae66

เราแค่ต้อง bruteforce ตาม wordlist ที่เขาให้มาโดยเอา word ไปแปลงเป็น md5 ก่อน bruteforce เมื่อ bruteforce แล้วก็เอาข้อความแต่ละอันไป decode hex กลับมา

```python
from Crypto.Cipher import AES
import hashlib
import random
import codecs

def decrypt(ciphertext, password_hash):
    ciphertext = bytes.fromhex(ciphertext)
    key = bytes.fromhex(password_hash)

    cipher = AES.new(key, AES.MODE_ECB)
    try:
        decrypted = cipher.decrypt(ciphertext)
    except ValueError as e:
        return {"error": str(e)}

    return {"plaintext": decrypted.hex()}

cipher = "c92b7734070205bdf6c0087a751466ec13ae15e6f1bcdd3f3a535ec0f4bbae66"

with open("word.txt", "r") as f:
    for line in f:
        password = line.strip()
        password_hash = hashlib.md5(password.encode()).hexdigest()
        result = decrypt(cipher, password_hash)
        try:
            print(f"{password} -> {codecs.decode(result['plaintext'], 'hex').decode('ascii')}")
        except:
            pass
```

```bash
python bruteforce.py
bluebell -> crypto{k3y5__r__n07__p455w0rdz?}
```

```
crypto{k3y5__r__n07__p455w0rdz?}
```
