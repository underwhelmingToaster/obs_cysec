
> [!tldr] Public Key Infrastructure (PKI)…
> …is a set of roles, policies, procedures, hardware and software which are used to manage certificates (distribution, usage, revoking etc.) and public-key encryption.
>

## 1 Structure
A PKI consists of:
- **Certificate authority (CA)**: stores, issues and signs certificates
- **Registration authority (RA**): Verifies identity of entities which are requesting digital certificates from the CA.
- **Validation Authority (VA):** Provides validation of PKI certificates. This can be done using:
	- **Certificate revocation list (CRL):** List downloadable over HTTP containing revoked certificates
	- **Online Certificate Status Protocol (OCSP):** Protocol used to obtain revocation status of a certificate. A request containing the Certificate Serial Number is sent to _OCSP responders_, which look up Certificate Status in a database and send back a signed response.

## 2 Certificate Pinning
Also called HTTP Public Key Pinning (HPKP), in Certificate Pinning Mode, the client has a preconfigured list of certificates it will trust.

### 2.1 Functionality
1. Browser connects to a site for the first time using HPKP
2. Browser records the public key from the header
3. From now on, only this key is accepted when connecting to this site, up to the "max-age" as defined by the website

#### 2.1.1 Pinning Models
- Pin the root
- Pin the intermediate CA
- Pin the end entity certificate (also called the “ssh model”)

> [!Success] Pros
> - Prevents certain types of cyberattacks

> [!fail] Cons
> - Key Compromise gets undetected (no certificate status checked)
> - complex maintenanence due to changing lists
> - reduced flexibility with changing servers
> - lacking scalability
