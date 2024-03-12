also known as Public Key Encryption

> [!tldr] Asymmetric Cryptography
> **Pros:**
> - Simplifies key distribution and management
>
> **Cons:**
> - Does not provide two-way encrypted communication

> [!example] Examples of Assymetric Encryption
> - [[RSA (Rivest–Shamir–Adleman)]]

## 1 Definition
In Asymmetric Cryptography, there is a **public key**, accessible to the public, and a **private key**, to which only the owner/creator of the public key has access to.

## 2 Functionality
Using asymmetric Encryption, two main Purposes can be fulfilled:
1. Encryption that only the owner of the public key can read
	1. Achieved by encrypting message with public key.
2. Signing that must have been performed by the owner of the private key
	1. Achieved by hashing a message and encrypting the hash using the private key. A receiver can hash the message, decrypt the hashed key and check that the two hashes match.
