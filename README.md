# Block cipher and DES questions:

1.

2. Decryption the message bellow:

```text
47dadszk21/FYxbW9uPRjQWPzUKlJu52y//rhPEIFvM=
```

Source code for encrypting:

```python
from Crypto.Cipher import DES
import base64

message = '############################'

def hex2bytes(hex):
    return bytearray.fromhex(hex)

def pad(text):
    while len(text) % 8 != 0:
        text += "*"
    return text

def enc(text, key):
    cipher = DES.new(key, DES.MODE_ECB)
    return base64.b64encode(cipher.encrypt(text))


key = hex2bytes('################')
text = pad(message).encode()

with open('cipher.txt', 'wb') as f:
    f.write(enc(text, key))
```
