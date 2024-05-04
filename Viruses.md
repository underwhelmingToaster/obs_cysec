> [!error] Viruses
> Computer viruses have two main functions, propagation and destruction

## 1 Types of Viruses
### 1.1 Multipartite Viruses
A virus which uses more than one [[#2 Propagation Techniques|propagation technique]] to spread, making it more effective.

### 1.2 Stealth Virus
A virus which takes measures to hide itself and tool antivirus packages into not detecting them.

### 1.3 Polymorphic Viruses
Viruses which can modify their own code. This mainly helps in avoiding detection with[[#2.6 Detection Methods|signature-based algorithms]] which might be used by an Antivirus, thus allowing the virus to spread longer before a detection algorithm has been created.

### 1.4 Encrypted Viruses
 Viruses which encrypt themselves using cryptographic techniques. For each system, a different cryptographic key is used, giving the virus [[#1.3 Polymorphic Viruses|polymorphic attributes]].

### 1.5 Logic Bombs
Viruses which lie dormant until they are triggered by the fulfilment of a condition, for example:
- time and or date
- program launch
- website logon
- external server trigger

### 1.6 Trojan Horses
A software which appears friendly, but contains a virus.

### 1.7 Keystroke logging
Also known as a keylogger, this virus records keystrokes made by the user. This allows access to a users login data (usernames, passwords). Classifies as [[#1.10 Spyware/Adware|spyware]].

### 1.8 Ransomware
Ransomware infects a target machine and then uses encryption technology to encrypt files stored on the system with a key known only to the malware creator. The virus requires payment to unlock the files again.

### 1.9 Worm
Viruses which spread without requiring human input. A popular example of a worm is [stuxnet](https://en.wikipedia.org/wiki/Stuxnet).

### 1.10 Spyware
Monitors the actions of a user on an infected system and transmits data to an external system.

### 1.11 Adware
A virus which displays advertisements on infected computers. Commonly display pop-ups in browser, but can be functionally more advanced, e.g. redirecting to competitor websites bafter monitoring shopping behaviour.

## 2 Propagation Techniques
Once a virus is established on the system, it can use various techniques to spread further

### 2.1 Master boot record (MBR) infection
MBR viruses attack the bootable partition (the media a computer uses to load the OS) of a disk.

### 2.2 File infection
File infection viruses infect executable files such es `.exe`, `.bat` and `.com` files and inject themselves into the file. Easily detected by using comparing hash values or detecting file size changes.
![[file injection.png]]

### 2.3 Macro infection
A virus which is written in a macro language (a language embedded inside another application, e.g. Microsoft Word/Excel). Not as effective nowadays, as developers of applications containing macro languages have taken extensive measures to reduce the ease of access for macros to the system.

### 2.4 Service injection
Viruses which inject themselves into trusted system services such as svchost.exe, winlogin.exe, and explorer.exe. This allows them to circumvent detection by virus applications.

## 4 Antiviruses

> [!tldr] Summary
> An Antivirus software is a computer program used to prevent, detect, and remove malware.

### 4.1 Detection Methods
There are multiple ways to detect a virus:
- Signature-based: The antivirus maintains a database containing known characteristics of known viruses. System storage is periodically scanned and compared to said database to detect potential viruses.
	- This method does not offer protection of [[Hacking#1.1 Zero-day exploit|Zero-day-exploits]]
- Heuristic-based: The antivirus monitors software behaviour, looking for malicious actions. Potentially malicious actions include:
	- elevation of privilege level
	- alteration of unrelated/system files
- Data Integrity: These antiviruses keep track of hash values for files in order to detect and report file content changes for critical files.

### 4.2 Virus Removal Methods
After a virus is detected, it is dealt with using one or a combination of the following methods:
- Deletion of virus files
- Disinfection of infected but original non-malicious files
- Restoration of the system to a safe state using a backup
- Quarantining malicious files by transferring them to a sandbox

#todo continue page 53
