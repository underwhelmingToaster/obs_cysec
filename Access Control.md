
> [!TLDR] TLDR
> Access control is the management of relationships between subjects and objects.

## 1 Definitions
### 1.1 Object
Passive entity which provides information to subjects, e.g. files, DBs, services, programs

### 1.2 Subject
Active entity which accesses an object to receive information from or about an object.

### 1.3 Need-to-Know/Least Privilege
This principle ensures that subjects only have access to data they need to work. Least Privilege relies on having a accurate Job Description in order to assign accurate priviledges. 

## 2 Access Control Types
### 2.1 Preventive
Prevents unwanted or unauthorized control from occurring: fences, locks, antivirus software, firewalls

### 2.2 Detective
Attempts to discover or detect unwanted or unauthorized activity. Operates only after the fact: CCTV, intrusion detection systems (IDSs), violation reports

### 2.3 Corrective
Returns systems to normal after an unwanted or unauthorized activity in order to correct any problems: System reboot, backup and restore plan

### 2.4 Deterrent
Discourages violation of security policies: security badges, guards

### 2.5 Compensating
Options which are added to existing access controls to enforce security: data encryption

### 2.6 Directive
A directive controls the actions of subjects to encourage or force security: Security policy requirements or criteria, posted notifications, escape route exit signs

### 2.7 Recovery
An extension of corrective controls with more advanced or complex features: fault-tolerant drive systems, system imaging, server clustering

## 3 Steps of access control
### 3.1 Identification
The process of a subject claiming or professing an identity. A subject’s identity is typically labelled as, or considered to be, public information

### 3.2 Authentication
Requires the subject to provide additional information that corresponds to the identity they are claiming, e.g. a password, smartcard, token

#### 3.2.1 Types of Authentication
- **Type 1**: Something you know: Password/PIN
- **Type 2**: Something you have: Smartcard, USB Drive
- **Type 3**: Something you are/do: Finger Print, Face ID, Eye Scan

#### 3.2.2 Multi-Factor Authentication
Multi-Factor should always be of 2 or more different types, or it will be no stronger than 1 Type Authentication.

> [!warning] Strength of Types
> Authentication using Type 1 is considered the weakest, with Type 3 being the strongest. 2/3 Type Multi-Factor is always stronger than a singular type.

#### 3.2.3 Secondary Authentication Factors
- **Somewhere you are**: Determining the location of the subject using IP Addresses or Phone Number.
- **Somewhere you are not**: Using the same technologies, geolocation can be used to identify suspicious activity (geo-blocking)

### 3.3 Authorization
Authorization ensures that the requested activity or access to an object is possible given the rights and privileges assigned to the authenticated identity.

### 3.4 Access control models
#### 3.4.1 Discretionary Access Control (DAC)
Every object has an owner, and the owner can grant or deny access to any other subjects. Used in NFTS etc.

#### 3.4.2 Role Based Access Control
Users are assigned to roles, and roles are assigned privileges. Users in a role will have all privileges assigned to their role(s).

#### 3.4.3 Rule Based Access Control
Global rules for all users. Rules in this models are sometimes called filters or restrictions.

#### 3.4.4 Attribute Based Access Control
Access to Objects are controlled by rules which can include multiple attributes. Subjects have attributes such as ID, job roles, group memberships, memberships, management level, security clearance etc. Access to an object is only granted if all attributes are acceptable.

#### 3.4.5 Mandatory Access Control
Each Object has a security level in an hierarchical structure (e.g. Top Secret, Confidential). Each Subject possesses a certain level in this structure as well. Subjects can only access Objects which are at or below their level in the hierarchy

### 3.5 Authorization Mechanisms
A authorization mechanism it the principle with which access to an object is granted or denied to a subject.

#### 3.5.1 Implicit Deny
Access to an object is denied unless access is explicitly granted to a subject. Most widespread mechanism currently in use.

#### 3.5.2 Constrained Surface
Using interfaces to control what subjects can see or do. Users with full privileges have access to all parts of the application.

#### 3.5.3 Access Control Matrix
An access control matrix is a table that includes subjects, objects, and assigned privileges.

|             | file1.txt   | file2.sql | Socket s                 |
| ----------- | ----------- | --------- | ------------------------ |
| Alice       | read, write | write     | -                        |
| Bob         | -           | read      | append                   |
| Process 294 | -           | -         | open, read, write, close |
#### 3.5.4 Capability Table
Same as Access Control Matrix, but focused on one service. Essentially the same as one collumn on the ACM.

#### 3.5.5 Content-Dependent Control
Content-Dependent Control grants subjects access based on the information an Object contains. This is normally done dynamically.

#### 3.5.6 Context-Dependent Control
Context-Dependent Control only grants Subject access to an Object after a certain context in the system has been reached with previous actions/events.

## 4 Access Control Attacks
### 4.1 Access Aggregation Attack (passive/reconnaissance attack)
Aggregating multiple pieces of non-sensitive information and aggregating it to sensitive information.

### 4.2 Password attacks (brute-force)
Trying out every possible combination of a password. Can be done against online accounts, or offline accounts if one can manage to steal a database.

#### 4.2.1 Dictionary Attack
Instead of randomly guessing passwords, a dictionary attack uses "commonly used passwords" databases and may also "one-up" passwords (for example "password" -> "pa5sword" -> one character changed) in this dictionary.

#### 4.2.2 Birthday Attacks (brute-force)
A birthday attack focuses on finding collisions. One can reduce the success of birthday attacks by using hashing algorithms with enough bits to make collisions computationally infeasible, and by using salts.

#### 4.2.3 Rainbow-Table Attacks
This attack utilizes tables of pre-computed hashes to cut out hash-calculation times.

#### 4.2.4 Sniffer Attacks
Using a sniffer to intercept network traffic containing classified information. Can be avoided by using secure transmission protocols, using One-Time passwords and establishing physical security in your network.