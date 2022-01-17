# Block cipher and DES questions:

## 1.

## 2. Decrypt the message bellow:

```text
47dadszk21/FYxbW9uPRjQWPzUKlJu52y//rhPEIFvM=
```

Source code for encrypting:

```python
from Crypto.Cipher import DES
import base64

def hex2bytes(hex):
    return bytearray.fromhex(hex)

def pad(text):
    while len(text) % 8 != 0:
        text += "*"
    return text

def enc(text, key):
    cipher = DES.new(key, DES.MODE_ECB)
    return base64.b64encode(cipher.encrypt(text))

message = '############################' # this is the message to be encrypted
key = hex2bytes('################') # a good key? idk

text = pad(message).encode()

with open('cipher.txt', 'wb') as f:
    f.write(enc(text, key))
```
