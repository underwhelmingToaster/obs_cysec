The OWASP Top Ten is a standard awareness document for developers and web application security. Is often used as a security standard. It is comprised of [[Hacking#5.2 Web Application Attacks|web application vulnerabilities]].

## 1 OWASP 2021
### 1.1 A01 - Broken Access Control
- Allows hackers to bypass authorisation mechanism, resulting in them becoming Privileged users.

### 1.2 A02 - Cryptographic Failures
- Failure of secure data transfer
- Gives hacker useful post-exploit information
	- For example how to maintain persistent access.

### 1.3 A03 - Injection
- Previously OWASP Nr. 1
- Introducing hostile code into a program
	- The injection alters the program execution.

### 1.4 A04 - Insecure Design
- Broad category representing different weaknesses that originate by faulty design
- Insecure design is **not** the source for all other top 10 categories
	- There is a difference between insecure **design** and insecure **implementation**

### 1.5 A05 - Security Misconfiguration
- Lack of Security Controls or Incorrect Security Controls
- Highly common due to endlessly customizable software

### 1.6 A06 - Vulnerable and Outdated Components
- Can include:
	- OS
	- Web/App Servers
	- Data Management Systems
	- API's
	- Libraries, Runtime Environments

### 1.7 A07 - Identification and Authentication Failures
 - Weaknesses may occur if Application:
	 - permits automated/brute-force attacks
	 - permits usage of weak passwords
	 - uses weak credential recovery (such as knowledge-based answers)
	 - stores passwords unsecurely
	 - has missing/ineffective MFA (multi-factor authentication)
	 - handles session identifiers incorrectly (storing them in URL, reusing them after successful login)

### 1.8 A08 - Software and Data Integrity Failures
- Occurs when code/infrastructure does not protect against integrity violations
	- Example: Application relies on plugins from untrusted sources.

### 1.9 A09 - Security Logging and Monitoring Failures
- Without logging/monitoring mechanisms in place, security breaches will likely not be detected.
- The following things may be monitored:
	- Warnings and Errors
	- Application and API access requests
	- Penetration testing tools

### 1.10 A10 - Server-Side Request Forgery
- Occurs when a web application is fetching from a remote, user supplied resource without validating said URL.
	- Allows attacker to send request to unexpected destination.