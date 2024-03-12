> [!example] See also
>  - [[Symmetric Cryptography]]
>  - [[Asymmetric Cryptography]]
>  - [[Hashing Functions]]

## 1 Definitions and Concepts
### 1.1 Cipher
An encryption algorithm (a set of rules which dictate how en- and deciphering should be processed) is also called a cypher. When used on a text, it produces a ciphertext.

### 1.2 Nonce (Number only used once)
An often random, arbitrary number that can be used just once in a cryptographic communication.

### 1.3 Initialization vector (IV)
Random bit string that is XOR-combined with the message in order to create a unique string, reducing overlapping hashes.

### 1.4 Confusion
When Mapping between input and output of a hash function is confusing.

### 1.5 Diffusion
When changes in input lead to spread out changes in output.

### 1.6 Kerkhoff’s Principle
The principle that the security of an encryption depends on the secrecy of the key, not the algorithm.

### 1.7 Substitution–Permutation Network
![|400](https://upload.wikimedia.org/wikipedia/commons/c/cd/SubstitutionPermutationNetwork2.png)
Series of linked Substitution and Permutation Blocks which are given the same key to produce a ciphertext.

#### 1.7.1 Substitution
To replace bytes or group of bytes with others in a one-to-one relationship to ensure reversibility.

#### 1.7.2 Permutation
Change position of bytes or byte groups within the message.

## 2 XOR

> [!NOTE] XOR Functionality
> Takes 2 inputs and outputs a 0 if the two inputs are equal, else it will output a 1.

XOR can be used to encrypt a message with a key. This requires a key which is the same length as the message. Given message **B** and key **A**, B can be encrypted by XOR'ing it with A and decrypted again by applying A a second time.

> [!tip] Perfect Secrecy
> If you take away the key, there is no way to find the message because there is no statical mapping between the input and the output.
