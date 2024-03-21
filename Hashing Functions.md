A hashing function takes a message of any length, and returns a pseudorandom hash of fixed length. A 128-Bit hashing function will produce 128-Bits of hash, regardless of message input length.

> [!example] Examples of hashing functions
> - MD5: completely broken
> - SHA1: also broken, see [shattered.io]()
> - **SHA2: current standard using 256/512bits**
> - SHA3: not better than SHA-2 but uses different hashing function
> - PBKDF2 (Password-Based Key Derivation Function 2): A intentionally slow algorithm for hashing passwords
> - Bcrypt: Similar to PBKDF2, but isn't easily parallelizable and is therefore not easily brute-forced

> [!tldr] TLDR
> Hashes…
> - are a one-way function (no way to reverse a hash to its original contents)
> - are fixed length

## 1 Hash Functions
Hash functions…
- need to be quick, but not too quick as to not allow an easy breaking of any hash
- need to introduce diffusion (small changes in input result in large changes in output)
- need to be non reversible
- need to guarantee that given a message and its hash, we can’t find another message that hashes to the same thing

## 2 Use Cases
### 2.1 Digital Signature
[![Alice signs a message—"Hello Bob!"—by appending a signature computed from the message and her private key. Bob receives the message, including the signature, and using Alice's public key, verifies the authenticity of the signed message.](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Private_key_signing.svg/220px-Private_key_signing.svg.png)](https://en.wikipedia.org/wiki/File:Private_key_signing.svg)
The sender of a message can sign a message by encrypting it with his private key and including this encryption after the unencrypted message. Recipients of this message can verify that a message was sent by the owner of the private key by using a _signature verifying algorithm_ which, given a message, a public key and signature, proves the authenticity of the message.

### 2.2 Ensuring a message has not been altered
