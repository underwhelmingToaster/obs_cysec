Symmetric key algorithms rely on a “shared secret” key that is distributed to all members who participate in the communications.

> [!tldr] Symmetric Cryptography
> **Pros:**
> - Very fast
> - Because AES is standardized, modern Processors often include an AES instruction set
> **Cons:**
> - To establish communication, the key must be exchanged using a secure channel (this can be done using [[Diffie-Hellman Key-Exchange]])
> - does not implement nonrepudiation (here is no way to prove where a given message originated)

## 1 Stream Ciphers
Take an input of possibly endless size and convert it to ciphertext.
- Encryption of long continuous streams, possibly of unknown length
- Extremely fast with a low memory footprint, ideal for low-power devices
- If designed well, it can seek to any location in the stream

- The keystream must appear statistically random
- You must never reuse a key + nonce
- Stream ciphers do not protect the ciphertext (= no guaranteed integrity)

## 2 Block Ciphers
Block ciphers take an input of a fixed size and return an output of the same size.

### 2.1 Modes of Operation for Block Cyphers
However, it is unlikely that a message is exactly as long as a given key. Therefore, there need to be ways to encrypt messages that are longer or shorter.

#### 2.1.1 Electronic Code Book (ECB)
Encrypt each block one after the other. Weak, especially for data with repeating patterns -> not recommended.

#### 2.1.2 Cipher Block Chaining (CBC)
XOR the output of each cipher block with the next input. This means that the cypher of one block will become the key for the next block. This process is safer than ECB, but not parallelizable.

#### 2.1.3 Counter Mode (CTR)
Encrypting the nonce, but for each block the nonce is increased by a value of 1. This encrypted number is then XOR'ed with the message to create the stream.
- Standard for all encryptions (AES)
- Can be parralelized

## 3 AES
#todo
