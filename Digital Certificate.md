## 1 Digital Certificate Issuance
### 1.1 Definitions
- **Certificate authority (CA)**: A authority which issues certificates to servers after they have done some research to prove that the website is what it says it is.

### 1.2 Process
1. A browser requests a website from a server.
2. The server sends back its certificate containing:
	- The servers public key
	- The [[Hashing Functions#2.1 Digital Signature|Digital Signature]] provided by the CA containing Name of the CA, Name of server and the signature hash
	- Some more extension fields
3. The browser can verify the authenticity of the issued Certificate by using the public key of the CA. This is called **chain of trust**.

## 2 Chain of Trust
![[Chain of trust.png|500]]
There still needs to be a way to verify that the CA is who they claim to be. In the internet, a website is almost always signed by a Root CA certificate, but an Intermediate CA Certificate, which itself may be signed by more intermediate certificates. The browser of a client will automatically validate each certificate until it reaches a **Root CA certificate**. Such certificates are saved in the trust store on the clients browser and are self-signed. Only if all certificates are validated by their respective chained parent certificate is the connection regarded as secure.

## 3 Trust Service Provider
TSP #todo
