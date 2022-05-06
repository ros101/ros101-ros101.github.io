---
layout: notes
---
# Encryption in Python

I extended [my custom shell](../unit7/michelle) with two new commands: ENCRYPT and DECRYPT.

The commands are two simple examples to encrypt and decrypt a file using Fernet in Python

Full sourcecode on [https://github.com/ros101/michelle](https://github.com/ros101/michelle)

```python
def do_encrypt(self, _, params):
    """encrypts a file"""
    # gets the password
    input_password = getpass.getpass('password: ')
    # some magic to encode the password, add salt and create the context
    password = input_password.encode('utf-8')
    salt = _get_salt()
    kdf = PBKDF2HMAC(algorithm=hashes.SHA256(), # the algorithm
                     length=32,
                     salt=salt,
                     iterations=390000) # increase iterations to make it stronger
    key = base64.urlsafe_b64encode(kdf.derive(password))
    fernet = Fernet(key)
    try:
        # actual encryption
        with open(params[0], 'rb') as input_file:
            # this reads the whole file, it's not suitable for large inputs
            data = input_file.read()
            # encrypts in memory, also not optimal
            encrypted_data = fernet.encrypt(data)
            # finally writes the output with .enc as a suffix
            with open(f'{params[0]}.enc', 'wb') as output_file:
                output_file.write(encrypted_data)
    except Exception as exception:
        _print(exception, Fore.YELLOW)

def do_decrypt(self, _, params):
    """decrypts a file"""
    # gets the password
    input_password = getpass.getpass('password: ')
    # same as for the encryption
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
            # this reads the whole file, it's not suitable for large inputs
            data = input_file.read()
            # dencrypts in memory, also not optimal    
            decrypted_data = fernet.decrypt(data)
            # finally writes the output with .dec as a suffix
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
    """generates a salt for the encryption"""
    salt_file_name = '.salt'
    if not os.path.exists(salt_file_name):
        # save the salt locally
        with open(salt_file_name, 'wb') as salt_file:
            salt_file.write(os.urandom(16))
    # return current salt: don't forget to backup it!
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
