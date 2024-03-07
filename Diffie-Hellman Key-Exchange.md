

> [!Warning] Prequisites
> - **Primitive Root**: g is a primitve root of p, when every number a that is relatively prime to p can be generated using $a \equiv g^{n}\pmod {p}$
> - **Discrete Logarithms Problem**: Consider $a^{b} \pmod{n} = c$ While it is easy, when given all other parameters, to calculate c, it is computationally expensive to calculate b.

## 1 Process
Alice and Bob want to generate a shared key over a public medium.
1. Alice and Bob agree on two large primes: **p** & **g**, where g is a primitive root of p.
2. Alice and Bob each select **a** & **b**, which are random numbers between 1 and p, as private keys.
3. Alice and Bob each calculate their public key. (It is infeasible to revert this process due to the Discrete Logarithm Problem)
	1. Alice calculates $g^{a} \pmod {p}$
	2. Bob calculates $g^{b} \pod {p}$
4. Alice and Bob exchange their calculated public key over the public medium.
5. Both add their private key with the received public key. This results in both parties having the shared secret key $g^{ab} \pmod{p}$.

Note that while this theoretically already permits the key to be used in [[Symmetric Cryptography]], usually this key is called a pre-master secret and is used to derive session keys. This could be done using SHA-256.

## 2 Attacking DHKE
The only way to find a or b is to solve:
$$a=\log_{g,p}(\text{g b})$$
$$b=\log_{g,p}(\text{g a})$$
## 3 Elliptic Curve Diffie-Hellmann Ephemeral-Verfahren (ECDHE)
A replacement for the mathematics enabling regular Diffie-Hellman. This methods the discrete logarithm problem is more difficult to solve than for regular DH.
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Adding_P%2CQ.PNG/170px-Adding_P%2CQ.PNG)](https://de.wikipedia.org/wiki/Datei:Adding_P,Q.PNG)

## 4 Ephemeral Mode
In this mode, a new key exchange is forced for each session. This increases security.
