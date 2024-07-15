- https://drive.google.com/file/d/1mgo-OBPx24RTJ46Qay2WUzg8P3CGRmO0/view
- https://www.reddit.com/r/WGU/comments/lhgi48/passed_1st_attempt_updated_study_guide_c172/?utm_source=share&utm_medium=ios_app&utm_name=ioscss&utm_content=2&utm_term=1
## Risk Management

1. Identify Risks
	1. **Quantitative risk assessment** is an approach in which the cost or value of the identified risk and its financial impact are examined. By quantifying risks, a financial business decision can be made in alignment with a risk transfer strategy (e.g., buying more insurance coverage).
	2. **Qualitative risk assessment** is an approach in which the risk impact is examined by assigning a rating for each identified risk (e.g., critical, major, or minor or high, medium, or low). When performing a qualitative risk assessment, the assessor must examine both the risk impact and the likelihood of occurrence.
2. Assess and Prioritize Risks
3. Plan Risk Response
4. Implement Risk Responses
5. Monitor and Control Risk Responses
6. Identify Risks

**Risk** is the likelihood that something bad will happen
**Threat** is something bad that might happen to an organization
**Vulnerability** is any exposure that could allow a threat to be realized. 
**Impact** refers to the amount of risk or harm caused by a threat or vulnerability that is exploited by a perpetrator.
**Event** is a measurable occurrence that has an impact on the business. either having little effect or perhaps escalating into an incident. 

## Cloud & Wireless Security

- Private Cloud - All hardware and software  required to provide services, including the network infrastructure is operated by a single org.
- Community Cloud - Shared infrastructure
- Public Cloud 
- Hybrid Cloud
### Access Control Modes

For people/orgs
- Discretionary Access Control (DAC) - you manage your own access control
- Role-based Access Control (RAC) - allows for server access control management
- Attribute-based Access Control (ABAC) - allows for additional attributes for access control (time/location)

For networks/firewalls
- Rule-based access control (RuBAC) - firewall rules
- Context-based access control (CBAC) - looks not just the contents of the packet but also the packets around that packets to get context

### Classification of Data
- Sensitive - Highest classification, release would cause great harm to the enterprise.
- Confidential - Medium classification, release would cause some harm to the enterprise
- Private - Must be protected but likely will not cause harm to the enterprise if release (for example, some types of PII)
- Public - Available to be released to the public that will not cause harm or will cause very little harm to the enterprise

*In what state is the data*
- Data in transit - Data being transmitted between two end-points
- Data at rest - Data being stored in some type of persistent media.
- Data in use - Data actively being processed or stored in memory

*What controls do you use* - CIA TRIAD
- Confidentiality - Encryption, file system permissions
- Integrity - Hashing, checksums, file system permissions, digital signatures
- Availability - Redundancies, off-site backups, cloud synchronization

### Malware Analysis and Remediation
- Antivirus/Antimalware Scanner
	- Rootkit Scanner
	- PUP scanner
	- Keystroke logging scanner
- Firewalls
- Anti-Spyware
- Intrusion Detection System

## Cryptography

Identity-based encryption - Uses the encryptor's identity to derive a key
Attribute-based encryption - Uses descriptive attributes to encrypt and decrypt data

Diffie-Hellman algorithm used modular arithmetic to generate keys, and Elliptic Curve DHE (ECDHE), which uses algebraic curves to generate keys. Both DHE and ECDHE use ephemeral key (i.e., cryptographic keys that are created as new keys for each new session) exchanges, which help make communications sessions more secure. Because each new key exchange uses new asymmetric keys, each communications session setup process is unique. Therefore, if a current session’s keys are compromised by an attacker, none of the previous session keys are at risk, a property that is called perfect forward secrecy .  

Quantum cryptography uses photons and their unique properties transmitted across an optical fiber channel to create an unbreakable cryptosystem. 
- Instead of bits, quantum cryptography uses qubits which can maintain a superposition of both values 0 and 1, at the same time.
- Shor / Grover algorithms are capable of breaking today's asymmetric and symmetric cryptographic algorithms given a large enough quantum computer

When it comes to information security, cryptography can satisfy these requirements: Confidentiality Integrity Authentication
 - **Confidentiality** -keeps information secret from unauthorized users. Makes information unintelligible to anyone who does not know the encryption cipher and the proper key.
 - **Integrity** - ensures that no one, including the sender, changes information after transmitting it. In addition, cryptography can enforce integrity with hashes or checksums. 
 - **Authentication** - Confirms the identity of an entity.
	 - Example - Microsoft NT LAN Manager (NTLM) protocol suite
 - **Nonrepudiation** - Prevents a party from denying a previous statement or action. Using asymmetric key cryptography, you can prove mathematically that a party did indeed originate a specific message at a specific time. 

The fundamental principle of asymmetric key cryptography is that it uses a key pair to encrypt and decrypt and the originator is the only one who knows one of the keys, which has an irrefutable timestamp.

### Data in Transit

**Data State**
- Passive - a file or data that is currently not being used
- In process - a file that is being edited, or data being altered
- In transit - files or data being uploaded, downloaded, synchronized

Data Protection Methodologies
- ACLs
- Database Object Permissions
- Implement authentication and Key Management methodologies
- Storage encryption
- Backup/restore
- Auditing
- Transport Level encryption
- Firewalls
- Server Hardening
- Physical Security
- Physical Hardware failover topologies at data centers

## Application Access Control

### Security Operations and Administration Chapter Notes

Security Operations Center (SOC)

Four Aspects of Access Control
- **Identification** - Assertions made by users about who they are
- **Authentication** - The proving of the assertion
- **Authorization** - The permissions a legitimate user or process has on the system
- **Accounting** - Tracking or logging what authenticated and unauthenticated users do while accessing the system

The four aspects of Access Control are divided into two phases:
- **Policy Definition Phase** - The authorization definition process operates in this phase to determine who has access and what systems or resources they can use.
- **Policy Enforcement Phase** - The identification, authentication, authorization execution, and accountability processes operate in this phase to grant or reject requests for access based on the authorizations defined in the first phase.

**Logical Access Controls** - 

**Physical Access Controls** - Ex. Smart card


#### Security Kernel
1. User requests access to an object. Kernel intercepts the request
2. Refers to its rule base, or security kernel database. It uses the rules to determine access rights.
3. Allows or denies access based on the defined access rules. All requests are logged for later tracking.

#### SSO Processes
- Kerberos - Protocol established by MIT that allows nodes communicating over a non secure network to identify one another in a secure manner. 
	- User sends ID and access request through Kerberos client
	- Kerberos Key Distribution Center (KDC) - Authentication server verifies that the usr and the requested service are in the KDC database, and if they are, sends a ticket, which is the user's unique time-stamped key for the service. 
	- If the ticket is not used within the designated time, it will not work.
- Secure European System for Applications in a Multi-Vendor Environment (SESAME) - Developed by the European Commission to address weakness in Kerberos. Is essentially an extension which improves key management by using both symmetric and asymetric keys.
- LDAP - Open source. Handles access control credentials. 
	- Does not provide a complete SSO  solution, it is part of most solutions. 

Documentation examples needed by the Security Administration
- Sensitive Assets list - What must be secured? 
- Security Process - Supporting documentation of how the process works
- Authority of the persons responsible for security - Which administrator is responsible or authorized for what assets and actions?
- Policies, procedures, and guidelines adopted by the organization - What information needs to be communicated, how is it communicated, and when is it communicated?

#### Access Control Models
**Bell-LaPadula** - Focuses on confidentiality of data and control classified information.
- Parts of a system are divided into subjects and objects, and the current condition of a system is its state
- Model guarantees that each state transition preserves security by moving from secure state to secure state, which is a process that ensures the systems meets the model's objectives. 

**Biba Integrity Model**
- The first part says a subject cannot read objects that have lower level of integrity than the subject does. A subject at a given level can only read objects of that level or higher.
- Subject cannot change objects that have a higher level
- Subject may not ask for service from subjects that have a higher integrity level. 

**Clark-Wilson Integrity Model**
- Stops unauthorized users from making changes
- Stops authorized users from making improper changes
- Maintains internal and external consistency

  Two important parts of this model
  - Three access entities - subject, program, and object - combine to form the access triple
  - Integrity is enforced by binding. Creates separation of duties, enforces integrity, and makes sure that only authorized transactions can be performed. 

**Brewer-Nash Integrity Model** - Can separate competitor's data within the same integrated database to make sure users do not make fraudulent changes to objects that belong to a competing organization, and stop users or clients from using data when they have conflict of interest. 

#### Authentication, Authorization, and Accounting (AAA) Servers

##### Centralized Access Control
**RADIUS** - Remote Authentication Dial-In User Service (Most popular)
 - Client config file that contains the client address and the shared secret for transaction auth
 - User config file that contains the user identification and authentication data as well as the connection and authorization information.

  Steps in auth process
  1. NAS decrypts the user's UDP access request
  2. NAS authenticates source
  3. NAS validates the request against the user file
  4. NAS responds by allowing or rejecting access or by requesting more information

**TACAS+** - Terminal Access Controller Access Control System Plus
 - Uses single config file to: 
	 - Control server operations
	 - Define users and attribute/value pairs
	 - Control authentication and authorization procedures

  Steps in auth process
  1. Using TCP, the client sends a service request with the header in cleartext and encrypted body containing the user ID, password, and shared key
  2. The reply contains a permit/deny as well as attribute/value pairs for the connection configuration

**DIAMETER** - Protocol based on RADIUS that defines how a AAA server should communicate and operate.
- Includes base protocol - defines the message format, transport, error, reporting, and security used by all extensions.
- Extensions - Conduct specific types of authentication, authorization, or accounting transactions.
- Uses UDP in P2P mode rather than client/server mode. 
	- A user provides another user with direct access to his or her hard drive, and in turn the second user also has access to the first user's hard drive. 

**SAML** - Security Assertion Markup Language
- Open standard based on XML 

##### Decentralized Access Control
- Password Authentication Protocol - uses cleartext usernames and passwords
- Challenge-Handshake Authentication Protocol - hashes the password with a one-time challenge number to defeat eavesdropping based replay attacks. 
- OATH
