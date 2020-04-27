# Signature and asymetric encryption in Python
>payload
```
file to sign
```
>init.py
```python
from Crypto.Hash import SHA512
from Crypto.PublicKey import RSA
from Crypto.Signature import PKCS1_PSS

MODE_WRITE_BYTE = 'wb'

print('starting generate key')
pair = RSA.generate(4096, progress_func=lambda key_parameter: print(key_parameter))

with open('private.pem', MODE_WRITE_BYTE) as file:
    file.write(pair.exportKey())
with open('public.pem', MODE_WRITE_BYTE) as file:
    file.write(pair.publickey().exportKey())

with open('payload', 'rb') as file:
    file_content = file.read()

content_hash = SHA512.new(file_content)

signature_scheme = PKCS1_PSS.new(pair)
signature = signature_scheme.sign(content_hash)

with open('signature', MODE_WRITE_BYTE) as file:
    file.write(signature)

######################################################################
# encryption part

encrypted_content = pair.encrypt(file_content, 'none')[0]

with open('encrypted_payload', MODE_WRITE_BYTE) as file:
    file.write(encrypted_content)
```
>verify.py
```python
from Crypto.PublicKey import RSA
from Crypto.Hash import SHA512
from Crypto.Signature import PKCS1_PSS

MODE_READ_BYTE = 'rb'

with open('public.pem', MODE_READ_BYTE) as file:
    public_key = file.read()

pair = RSA.importKey(public_key)

with open('payload', MODE_READ_BYTE) as file:
    file_content = file.read()

with open('signature', MODE_READ_BYTE) as file:
    signature = file.read()

content_hash = SHA512.new(file_content)

signature_scheme = PKCS1_PSS.new(pair)
verification = signature_scheme.verify(content_hash, signature)

print(verification)

######################################################################
# encryption part

with open('private.pem', MODE_READ_BYTE) as file:
    private_key = file.read()

pair = RSA.importKey(private_key)

with open('encrypted_payload', 'rb') as file:
    encrypted_content = file.read()

content = pair.decrypt(encrypted_content)

print(content.decode())
```