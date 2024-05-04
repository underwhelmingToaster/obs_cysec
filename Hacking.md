## 1 Terminology
### 1.1 Zero-day exploit
A vulnerability or security hole in a system unknown to its owners, developers or anyone capable of mitigating it.

### 1.2 Demilitarized zone (DMZ)
A DMZ refers to a segregated network segment that sits between an organization's internal network and an external network (typically the internet). This typically insures that, for example, the database of an application is only accessible to the webserver, and not directly to the internet.
![|500](https://upload.wikimedia.org/wikipedia/commons/5/52/DMZ_network_diagram_1_firewall.png)

## 2 Types of Hackers
- **Black Hat:** Malicious, destructive hacker that usually remains anonymous
- **Grey Hat**: Those possessing Black hat skills who focus on both offense and defense
- **White Hat**: Those possessing black hat skills who primarily focus on defense
- **Script Kiddie**: Individuals that use tools without understanding what they are doing
- **Cyber Terrorist**: Skilled attacker whose purpose it to further an ideology
- **State Sponsored**: Hackers employed by the government for both offensive and defensive activities

## 3 Threat Sources
- **Script Kiddie:** Attacks of script kiddies who are deploying ready-to-use software.
- **Drive-by download:** A download which is either
	1. authorized by a user without understanding what is being downloaded ([[Viruses#1.6 Trojan Horses|trojan]]) or
	2. a download which occurs without a user's knowledge using security flaws in software
- **Advanced persistent threat (APT):** Adversaries with advanced technical skills and significant financial resources, often equipped with [[#1.1 Zero-day exploit|zero-day exploits]].

## 4 Ethical Hacking
Using tools and techniques to validate, audit and report on system/software vulnerabilities

### 4.1 Penetration Testing
The manual process of trying to uncover weaknesses in a system.

#### 4.1.1 Methods of Penetration Testing
- Black-Box Testing: Penetration Tester has no internal knowledge of target system.
- Grey-Box Testing: Penetration Tester has knowledge of a system user, potentially with elevated privileges.
- White-Box Testing: Penetration Tester has full access to source code.

### 4.2 Vulnerability Scanning
Automated Process of Scans, searching for Attack Opportunities, deprecated Systems/Versions

## 5 Attacks

### 5.1 Application Attacks
#todo was isch de abschnitt überjaupt
#### 5.1.1 Buffer overflow
A buffer overflow vulnerability exists when user input is not properly validated, thus allowing to read or write past the memory space reserved for a field.

#### 5.1.2 Time of Check to Time of Use
A timing vulnerability that occurs when a program checks access permissions too far in advance of a resource request, allowing the attacker to use this _window of vulnerability_ to get access to a file.

#### 5.1.3 Back Door
A way to access a computer system or encrypted data that bypasses the system's customary security mechanisms. This could be purposefully implemented by a developer for troubleshooting or other purposes.

#### 5.1.4 Escalation of Privilege
When a hacker or virus elevates his privileges beyond the aim of a system administrator. Such escalations may be done with a **rootkit**, which exploit known vulnerabilities of a system.

### 5.2 Web Application Attacks
Note the [[OWASP Top 10]] for the ten most prevalent security vulnerabilities.

#### 5.2.1 Cross-Site Scripting (XSS)
A XSS Attack occurs when a hacker injects malicious code into an otherwise legitimate website to cause harm. Code can be injected in the form of `<script>` tags. There are three main XSS attacks:

##### 5.2.1.1 Non-Persistent (Reflected) XSS
Occurs when HTTP-GET or HTTP-POST parameters are not sanitized. This allows an attacker to execute scripts on the website directly. A hacker might send links to legitimate URLs, but malicious parameters, to victims.

> [!example]
> Take a website which stores search field value in the URL. (HTTP-GET)
> `http://example.com/?search=Car`
>
> A attacker might utilize this by injecting code like this:
> `http://example.com/?search=<script type="text/javascript">alert("XSS")</script>`
> which will result in this code being executed by the server.

##### 5.2.1.2 Persistent (stored) XSS
This type of XSS differs from Reflected XSS in the fact that malicious code is stored on the server. This requires, that user input is saved and later displayed again, while not being sanitized at any stage.

> [!example]
> Take a website which implements a guest book.
>
> An attacker would make a new entry into this guest book, similar to this:
> `Nice Page!<script type="text/javascript">alert("XSS")</script>`
>
> This would result in the injected code being executed for each user which opens this page.

##### 5.2.1.3 DOM-based (local) XSS
In case a web application does not necessarily communicate with its web server (e.g. AJAX), local XSS is used instead. Local XSS is similar to reflected XSS, with the difference that the malicious data never comes into contact with a webserver, but is instead processed on the users machine.

#### 5.2.2 Cross-Site-Request-Forgery (CSRF)
In a CSRF attack, an attacker tricks a user into unknowingly making a request on a web application that the user is authenticated with.

> [!example]
> [Source](https://www.youtube.com/watch?v=vRBihr41JTo) Your Online Bank lets you transfer money using an online form which has two fields: "Destination IBAN" and "Amount" (of money to transfer). In normal use, you fill out the form and hit submit. The data gets sent to the bank using HTTP-POST, which processes it.
>
> Now, while logged into their E-Banking Application in another tab, a victim enters an malicious website. This website seems normal, but has two hidden fields: "Destination IBAN" and "Amount", which are already pre-filled with the IBAN of the hackers account and, for example, 1000 CHF.
>
> The malicious website then sends a HTTP-POST request to the bank. The bank server sees the necessary fields and performs the transaction, as does not check to validate that the request actually comes from the E-Banking Application.  

CSRF attacks can be mitigated by implementing CSRF-Tokens, a secure token which an attacker would not be able to know and therefore can't embed into the POST request.

#### 5.2.3 SQL Injection
A type of security vulnerability that occurs when an attacker is able to manipulate SQL queries executed by a web application's database. This vulnerability arises when user input is directly incorporated into SQL queries without validation or sanitization.

> [!example]
> A Bank allows you to get the balance of an account by entering its account number. This number is used to query the database as such:
> `SELECT * FROM transactions WHERE account_number = '<number>'`
>
> A hacker could utilize this by entering the following into the "number" input field: `'1234'; DELETE * FROM transactions WHERE 'a' = 'a’`. This would produce a query that will both
> 1. retrieve the balance for account number 1234
> 2. delete all transaction records from the database

### 5.3 Network Attacks
#### 5.3.1 Denial of Service (DoS)
Overwhelming a server with a flood of illegitimate traffic or requests. This renders the server unable to respond to legitimate traffic.
![[dos attack types.png]]

##### 5.3.1.1 SYN Flooding
A type of DoS attack. Flooding a server with TCP `SYN` segments, to which the server will reply with multiple `SYN ACK` packets and waits the corresponding `ACK` packets, which the attacker will not send. This half-opens a large number of connections, until a limit is reached. Legitimate users will then not be able to open new connections, as the server is occupied with waiting on `ACK` packets.

##### 5.3.1.2 Application Level DoS
DoS attack in which attacker sends malformed application packets which are utilizing certain weaknesses/exploits in software. Explotaition of such weaknesses will cause crashes, freezes and errors.

##### 5.3.1.3 Distributed DoS (DDoS)
Using a distributed botnet to carry out DoS attacks.

#### 5.3.2 Man in the Middle Attack
The attacker inserts itself between host and client, thus being able to eavesdrop on all communications without being detected.

#### 5.3.3 Man in the Browser Attack
Trojan Browser Plugin which captures inputs, highjacks authentication sessions and injects code into webpages.

#### 5.3.4 Replay Attack
Re-establish communications with a host by repeating credential information in a one to one fashion after a valid authentication session has been eavesdropped on.
