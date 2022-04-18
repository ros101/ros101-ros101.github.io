---
layout: notes
---
# Encryption in Python

I extended my custom shell with two new commands: ENCRYPT and DECRYPT

Full sourcecode on [https://github.com/ros101/michelle](https://github.com/ros101/michelle)

```python
  def do_encrypt(self, _, params):
    input_password = getpass.getpass('password: ')
    password = input_password.encode('utf-8')
    salt = _get_salt()
    kdf = PBKDF2HMAC(algorithm=hashes.SHA256(),
                     length=32,
                     salt=salt,
                     iterations=390000)
    key = base64.urlsafe_b64encode(kdf.derive(password))
    fernet = Fernet(key)
    try:
        with open(params[0], 'rb') as input_file:
            data = input_file.read()
            encrypted_data = fernet.encrypt(data)
            with open(f'{params[0]}.enc', 'wb') as output_file:
                output_file.write(encrypted_data)
    except Exception as exception:
        _print(exception, Fore.YELLOW)

def do_decrypt(self, _, params):
    input_password = getpass.getpass('password: ')
    password = input_password.encode('utf-8')
    salt = _get_salt()
    kdf = PBKDF2HMAC(algorithm=hashes.SHA256(),
                     length=32,
                     salt=salt,
                     iterations=390000)
    key = base64.urlsafe_b64encode(kdf.derive(password))
    fernet = Fernet(key)
    try:
        with open(params[0], 'rb') as input_file:
            data = input_file.read()
            decrypted_data = fernet.decrypt(data)
            with open('.'.join(params[0].split('.')[:-1]) + '.dec', 'wb') as output_file:
                output_file.write(decrypted_data)
    except Exception as exception:
        _print(exception, Fore.YELLOW)
```

with

```python
import base64
from cryptography.fernet import Fernet
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
import getpass
import os
```

and

```python
def _get_salt():
    salt_file_name = '.salt'
    if not os.path.exists(salt_file_name):
        with open(salt_file_name, 'wb') as salt_file:
            salt_file.write(os.urandom(16))
    with open(salt_file_name, 'rb') as salt_file:
        return salt_file.read()
```


I chose `Ferret` because it implements `AES 128` and `SHA-256` with at least 310.000 iterations, following OWASP recommendation.

This solution satisfies the GDPR requirements because it implements common industry standards that can satisfy art 32.

## References

GDPR (N.D) Art 32. Available from https://gdpr-info.eu/art-32-gdpr/

GDPR (N.D) Encryption. Available from https://gdpr-info.eu/issues/encryption/

OWASP (N.D) Cryptographic Storage Cheat Sheet. Available from https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html#algorithms

OWASP (N.D) Password Storage Cheat Sheet. Available from https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
