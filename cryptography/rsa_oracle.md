## rsa_oracle

Challenge description:
```
Can you abuse the oracle?
An attacker was able to intercept communications between a bank and a fintech company. They managed to get the message (ciphertext) and the password that was used to encrypt the message.
After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here nc titan.picoctf.net 51115. Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.
```

Hints:
```
Crytography Threat models: chosen plaintext attack.

OpenSSL can be used to decrypt the message. e.g openssl enc -aes-256-cbc -d ...

The key to getting the flag is by sending a custom message to the server by taking advantage of the RSA encryption algorithm.

Minimum requirements for a useful cryptosystem is CPA security.
```

Ciphertext link:
```
https://artifacts.picoctf.net/c_titan/148/secret.enc
```

Password link:
```
https://artifacts.picoctf.net/c_titan/148/password.enc
```

pwntools is installed to interact with the oracle. 

A script is written to decrypt the text based on the given challenge instance configurations. It is called ```decrypt_password.md```:
```
from pwn import *

context.log_level = 'critical'
p = remote("titan.picoctf.net", 51115)

p.recvuntil(b"decrypt.")

with open("password.enc") as file:
    c = int(file.read())

# Encrypting 2
p.sendline(b"E")
p.recvuntil(b"keysize): ")
p.sendline(b"\x02")  # Sending the value 2 in hexadecimal
p.recvuntil(b"mod n) ")

c_a = int(p.recvline())

# Decrypting (c * c_a)
p.sendline(b"D")
p.recvuntil(b"decrypt: ")
p.sendline(str(c_a * c).encode())
p.recvuntil(b"mod n): ")

password = int(p.recvline(), 16) // 2
password = password.to_bytes(len(str(password)) - 7, "big").decode("utf-8")

print("Password:", password)
```
This script first connects to the oracle.
Then it encrypts a known plaintext 2. The result is stored in ```c_a```.

The encrypted password ```c``` is multiplied by ```c_a``` and this result is sed for decryption. Dividing this result by 2 gives the password.

It is converted into bytes and decoded into a string from integer. 

We encrypt 2 as it can exploit the homomorphic property of RSA encryption, which allows multiplication on ciphertexts. 

```
D(c_a . c) = m1 . m2 = password . 2
```

We run the script:
```
python3 decrypt_password.md
```
Output:
```
Password: 24bcb
```

To decrypt using the password:
```
openssl enc -aes-256-cbc -d -in secret.enc
```

Output:
```
enter AES-256-CBC decryption password:
```

The password is entered and the flag is found as output:
```
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
picoCTF{su((3ss_(r@ck1ng_r3@_24bcbc66}
```
