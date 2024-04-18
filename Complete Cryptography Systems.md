## 1 Definitions
- **Message authentication code** (MAC): Short piece of information which authenticates and integrity-checks a message.
- **Authenticated Encryption** (AE): Authenticated Encryption (AE) is an encryption approach that addresses confidentiality and authenticity at the same time.
- **Perfect Forward Secrecy**: Assures that even if long-term secrets are compromised, session-keys are not compromised. This means that past sessions stay secure.

## 2 Types of Authenticated Encryption
 There are multiple approaches that aim to provide confidentiality and integrity at the same time.

### 2.1 Encrypt-then-MAC
_Used by IPSec_
- Generate two keys
- Encrypt the message with the first key
- Authenticate the encrypted message with the second key

### 2.2 Encrypt-and-MAC
_Used by SSH_
- Generate two keys
- Encrypt the message with the first key
- Authenticate the message (plain text) with the second key

### 2.3 MAC-then-Encrypt
_Used by [[SSL & TLS]]_
- Generate two keys
- Calculate the message authentication code using the first key
- Encrypt the message plus the message authentication code using the second key

### 2.4 Authenticated encryption with associated data (AEAD)
Variant of AE that allows the message to include "associated data" (AD, additional non-confidential information). This can be useful if, for example, a network header needs to be visible, but should be able to be validated.
