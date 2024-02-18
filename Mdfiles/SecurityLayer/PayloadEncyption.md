# Security Layer

## Payload Encryption

For Payload Encryption using AES Encryption with GCM Mode

This documentation provides a guide on how to use the `Crypto.Cipher` module in Python for AES encryption with GCM (Galois/Counter Mode) mode. GCM is an authenticated encryption mode that provides both confidentiality and integrity.

Dependencies:
- `pycryptodome`: This library is used for AES encryption and decryption.

Import the necessary key and configure developement.ini
    hexadecimal string : SECRET_KEY

Create an instance of the AESEncryption class for handling AES encryption and decryption:
   nonce : AESEncryption(settings.key_hex, secrets.token_hex(16)) 
    every api unique key set in the aes payload to secure the data.



In AES-GCM (Advanced Encryption Standard - Galois/Counter Mode), a nonce (number used once) is a value that should be unique for each encryption operation with the same key. It is combined with the key and the plaintext to produce the ciphertext. The uniqueness of the nonce is crucial for the security of the AES-GCM algorithm.

The nonce is usually a random or unique value, and it should not be reused with the same key. If a nonce is reused for the same key, it can compromise the security of the encryption and authentication provided by AES-GCM.

When working with AES-GCM, the combination of the key and nonce is used to produce a unique keystream for encrypting the plaintext and generating an authentication tag. The authentication tag is used to verify the integrity of the ciphertext during decryption.

Here's a simple example using the cryptography library in Python, which is a popular library for cryptography:

```
from cryptography.hazmat.primitives.ciphers.aead import AESGCM
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.backends import default_backend
import os

# Generate a random 96-bit nonce
nonce = os.urandom(12)

# Generate a random 256-bit key
key = os.urandom(32)

# Create AES-GCM cipher object
cipher = AESGCM(key)

# Encrypt the plaintext
plaintext = b"Hello, AES-GCM!"
ciphertext = cipher.encrypt(nonce, plaintext, None)

# Decrypt the ciphertext
decrypted_text = cipher.decrypt(nonce, ciphertext, None)

# Verify the authenticity of the ciphertext
try:
    # This should not raise an exception if the ciphertext is authentic
    cipher.decrypt(nonce, ciphertext, None)
    print("Authentication successful.")
except Exception as e:
    print(f"Authentication failed: {str(e)}")

print(f"Original Text: {decrypted_text.decode('utf-8')}")
```


https://pycryptodome.readthedocs.io/en/latest/src/examples.html#encrypt-data-with-aes