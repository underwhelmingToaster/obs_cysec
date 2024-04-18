The standard for defining the format of public key certificates as used in [[Public Key Infrastructure]]. It is used in many protocols, most notably in [[SSL & TLS]].

Nowadays, X.509v3 is the most commonly used version.

## 1 Structure of a Certificate (X.509v3)
- **Certificate**
	- Version Number
	- Serial Number
	- Signature Algorithm ID
	- Issuer Name
	- Validity period
		- Not Before
		- Not After
	- Subject name
	- Subject Public Key Info
	- Public Key Algorithm
	- Subject Public Key
	- Issuer Unique Identifier (optional)
	- Subject Unique Identifier (optional)
	- Extensions (optional)
		- …
- **Certificate Signature Algorithm**
- **Certificate Signature**

### 1.1 Components
#### 1.1.1 Serial Number
A positive integer which is unique for each certificate issued by the CA.

#### 1.1.2 Issuer Distinguished Name (DN)
Identifies the entity or Certificate Authority or self signing application that signed the certificate

#### 1.1.3 Signature Algorithm
Identifies the cryptographic algorithm used by a certificate authority to sign the digital certificate

### 1.2 Extension
Depending on the use case of the certificate, extensions are mandatory: e.g.
- root CA certificate
- signing certificate
- TLS profile certificate
- etc.

## 2 Types of certificates
### 2.1 Root CA Certificate
Self signed certificate

### 2.2 Intermediate CA certificate
Also called subordinate CA certificates.

### 2.3 End-entity certificate
A certificate that cannot issue other certificates. Identifies a user (person, organisation). Also called a leaf certificate.
