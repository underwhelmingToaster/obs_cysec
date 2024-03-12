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
- Digital Signature
- Ensuring a message has not been altered
