Cryptography - The development and use of codes
Cryptanalysis - The breaking of those codes

Cryptographic Hash Operation:
        Data goes through Hash Function and returns Hash Value
        h=H(x), x=data, h=Hash, H=Hash Function

hashing can be used to be check to integrity of data

HMAC Hashing Algorithm:
        Using a key with the data to create the hash value
        Hash Function(data + key) = Hash Value

Three primary objective of securing communications:
        Authentication - Guarantees that the message is not forgery
        Integrity - Guarantees that no one intercepted the message and altered it
        Confidentially - Guarantees that if the message is captures is cannot be deciphered

Asymmetric and Symmetric encryption are the two classes of encryption used to provide data confidentiality. These two classes differ in how they use keys.

Symmetric:
        - Use the same key to encrypt and decrypt
        - Keys are short
        - Faster and asymmetric
        - Commonly used for encrypting bulk data
                Keys are pre-shared
                KEY                 KEY
        DATA -> ENCRYPT -> HASH -> DECRYPT -> DATA

Asymmetric:
        - Used different keys for encryption and decryption
        - Keys are long
        - Computationally taxing so slower
        - Commonly used for quick data transactions
                EKEY                DKEY
        DATA -> ENCRYPT -> HASH -> DECRYPT -> DATA

DES or AES are Symmetric encryption

Public keys are used to encrypt data
Private keys are used to decrypt data

Diffie-Hellman https://www.youtube.com/watch?v=NmM9HA2MQGI&pp=ygUOZGlmZmllLWhlbGxtYW4%3D

# Math
Cryptography uses mathematics to scramble the text in a specific way.
Two operations used are XOR and Modulo.

## XOR
XOR -> exclusive OR
Compares two bits in binary and returns 1 if the bits are different and 0 if they are the same. (This operating is represented with ⊕ or ^)

|A|B|A ⊕ B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|
## Modulo
- Commonly written as % or mod.
- Gets the remainder of a division.
- X%Y = whats left
- 5 % 3 = 2
- Modulo is not reversible