## 1 History
- 1994: SSL 1.0 (unpublished)
- 1995: SSL 2.0
- 1996: SSL 3.0
- 1999: TLS 1.0 – RFC 2246, roughly identical to SSL 3.0
- 2006: TLS 1.1 – RFC 4346, Security fixes and removed some methods of encryption
- 2008: TLS 1.2 – RFC 5246  Authenticated encryption added, hashing function improved, many TLS extensions added
- 2018: TLS 1.3 – RFC 8446:
	- removed broken cryptography
	- remove broken features: compression and renegotiation
	- Added 1-RTT and 0-RTT, where so called "Early Data" is already sent during the handshake, even though it can only be decrypted after authentication is complete
	- Encrypting more of the protocol for privacy

> [!Error] Warning
> Protocols up until and including TLS 1.0 are considered seriously broken

## 2 SSL
Secure Socket Layer (SSL), now superseded by TLS, but often still used to describe TLS functionality.

## 3 TLS
TLS is the primary mechanism for encryption for HTTP communication, that is called HTTPS.

### 3.1 Definitions
- TLS Connection: A transient, peer-to-peer relationship. Every connection is associated with one TLS Session.
- TLS Session: A association created between a client and a server. Contains properties which are saved and used for multiple connections in order to avoid expensive renegotiation

### 3.2 Cipher Suites
Each cipher suite has a name which declares what technologies are used for TLS. An example TLS cipher suite name would be:
**TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256**
- TLS: defines the protocol that this cipher suite is for. 
	- Usually TLS
- ECDHE: indicates the key exchange algorithm being used 
	- RSA, DHE, ECDHE
- RSA: authentication mechanism during the handshake
	- RSA, DSA, ECDSA
- AES: block or stream cipher to be used
	- AES, ChaCha20
- 128: session encryption key size (bits) for cipher.
- GCM: type of encryption (cipher-block dependency and additional options)
- SHA256: Hash function with digest size in bits, used to authenticate the message:
	- MD5, SHA
### 3.3 Protocol
TLS Packets are layered on top of the TCP Layer. Each TLS Record starts with a record header of 5 Bytes followed by a Record body, which is encrypted.

In the Record header, the type of TLS record is declared. There are the following types:
- **Handshake Protocol (22):** ClientHello, ServerHello, Certificate, ServerHelloDone
- **Change Cipher Spec Protocol (20)**
- **Alert Protocol (21):** Warning, Fatal (Session is closed immediately)
- **Application Protocol (23):** Transmission of (encrypted) payload

### 3.4 Handshake

> [!Note] Note
> This is the TLS 1.2 version of the handshake. A wireshark recording can be found [[tls12-dsb.pcapng|here.]]

 ```mermaid
 sequenceDiagram
     participant A as Client
     participant B as Server
     A-)B: Client Hello
     B-)A: Server Hello
     B-)A: Certificate*
     activate B
     B-)A: Server Key Exchange*
     B-)A: Server Hello Done
     deactivate B
     A-)B: Certificate*
     activate A
     A-)B: Client Key Exchange
     A-)B: Client Change Cypherspec
     A-)B: Client Finished
     deactivate A
     B-)A: Change Cyphertext
     activate B
     B-)A: Server Finished
     deactivate B
     Note over A,B: Application Data can now be sent
 ```
_Messages connected with a bar are sent in one message._
_Messages marked with * are optional._

#### 3.4.1 Client Hello
The client sends the following information to a server it wants to connect with:
- TLS protocol version
- client random data (used later in the handshake)
- an optional [[#3.5 Resuming Session|session id to resume]]
- a list of cipher suites
- a list of compression methods
- a list of extensions

#### 3.4.2 Server Hello
The Server Responds with the following information:
- the selected protocol version
- server random data (used later in the handshake)
- the session id
- the selected cipher suite
- the selected compression method
- a list of extensions

#### 3.4.3 Server Certificate
The server responds with
- the hostname of the server
- the public key used by this server
- [[Digital Certificate]] from CA

#### 3.4.4 Server Key Exchange
The Server also sends parameters which set up a Key Exchange, in this case [[Elliptic Curve Diffie-Hellmann Ephemeral (ECDHE)]].  This step can be omitted if using RSA, for example, because the servers public key is already contained in the certificate.

#### 3.4.5 Client Key Exchange
The client sends their parameters for the Key Exchange.

#### 3.4.6 Client ChangeCypherSpec

> [!Warning]
> In TLS 1.3, this message has been removed because it can be inferred.

The client indicates that it has calculated the shared encryption keys and that all following messages from the client will be encrypted with the client write key.

#### 3.4.7 Client Handshake Finished
Connection parameter data is encrypted using the client write key and sent to the server. Only if the encryption is working as intended can the server decrypt and confirm the message.

#### 3.4.8 Server ChangeCypherSpec & Finished
The server sends a ChangeCypherSpec and a Finished Message with verification to ensure that the connection works both ways.

### 3.5 Resuming Session
In case the client has a session ID of a previous connection, the ID can be used to avoid having to negotiate a new encryption, instead using the parameters of the old session. In the case that the server still has the cryptographic context stored, the TLS Handshake will look like this:

 ```mermaid
 sequenceDiagram
     participant A as Client
     participant B as Server
     A-)B: Client Hello
     B-)A: Server Hello
     B-)A: Change Cyphertext
     activate B
     B-)A: Server Finished
     deactivate B
     A-)B: Client Change Cypherspec
     activate A
     A-)B: Client Finished
     deactivate A
     Note over A,B: Application Data can now be sent
 ```
### 3.6 Heartbeat Protocol
A periodic signal to indicate to the sender that the recipient is still alive. Use is established during the Handshake if both parties declare that they support heartbeat protocol in the [[#3.4.1 Client Hello]]/[[#3.4.2 Server Hello]]

The protocol works as follows:
1. Client sends a heartbeat request with a payload message
2. Server extracts message and sends same message back in heartbeat response message
3. Client verifies that the received payload is the same as the sent one 
#### 3.6.1 Heartbleed Exploit
TLS Heartbleed exploits the functionality of the Heartbeat protocol: A heartbeat request contains information about its own `length`. An attacker is sending a malformed heartbeat message which contains only a small message, but declares itself as a big one using the `length` property. If the server does not check to make sure that  `length` is correct, it will send back as much information as is declared in `length`, filling the message from memory, thereby causing a memory leak from which confidential information can be read.