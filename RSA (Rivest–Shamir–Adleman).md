## 1 Components
- Public Components:
	- **N**: A semi-prime (multiple of two Primes), usually very large (4096 bits)
	- **E**: A small number (commonly 3 or 65537)
- Private Components:
	- **D**: #todo

## 2 Process
1. Encrypt Message m to Cypher c with the public key using $c=m^{e}\pmod{n}$.
2. Owner Decrypts the Cypher c using $m=c^{d}\pmod{n}$

## 3 Weaknesses
### 3.1 Short Message
In the case that the message is short, RSA encryption would be very weak. To combat this, padding is added to short messages. The standard for this is Optimal asymmetric Encryption padding (OAEP). The server has to remove the padding again after the message is received and decrypted.

### 3.2 Performance
RSA is up to a 1000 times slower than symmetric cryptography.

## 4 Alternatives
Because RSA is utilizing the [[One-Way Trapdoor Functions#3 Factorization Problem|Factorization Problem]], which will become too slow in a few years, other ways for message signing need to be found.

### 4.1 Digital Signature Algorithm (DSA)
Much faster than RSA as it relies on the [[One-Way Trapdoor Functions|Discrete Logarithm Problem]] or a [[One-Way Trapdoor Functions#2 Elliptic Curve|Elliptic Curve]]. While it cannot be used for encryption, it provides a fast and secure signing of messages.
