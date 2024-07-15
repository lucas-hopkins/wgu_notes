
## TCP/IP Reference Model
Alternative to the OSI Model which defines __four__ layers instead of seven


|OSI Model| TCP/IP|

| OSI Model            | TCP/IP                 |
| -------------------- | ---------------------- |
| Layer 7  Application | Layer 4 \| Application |
| Layer 6 Presentation | Layer 4 \| Application |
| Layer 5 Session      | Layer 4 \| Application |
| Layer 4 Transport    | Layer 3 Host-to-Host   |
| Layer 3 Network      | Layer 2 Network        |
| Layer 2 Data Link    | Layer 1 Physical       |
| Layer 1 Physical     | Layer 1 Physical       |
### TCP-IP Reference Model Layer Summary
- __Application Layer__ - Interacts with applications that need to gain access to network services
- __Transport or Host-to-Host Layer__ - Segments data and adds a checksum to properly validate data to ensure that it has not been corrupted.
- __Network or Internet Layer__ - Handles packets as they move around the network
- __Physical or Network Access Layer__ - The point at which the higher-layer protocols interface with the network transport media.

#### Application Layer
Uses the following protocols:
 - Dynamic Host Configuration Protocol (DHCP)
 - Hypertext Transfer Protocol (HTTP)
 - Internet Message Access Protocol (IMAP)
 - File Transfer Protocol (FTP)
 - Post Office Protocol (POP)
 - Session Initiation Protocol (SIP)

#### Internet Layer
Responsible for sending packets across the network. 
Examines each packet, determines its destination and makes the necessary routing decisions to get the packet to its destination.

#### Network Access Layer
Scope of the Network Access Layer is the current LAN and interacts with the physical hardware.
Uses switching to direct packets to physical hardware
Uses the following protocol:
 - Address Resolution Protocol (ARP)
 - Layer 2 Tunneling Protocol (L2TP)
 - Point-to-Point Protocol (PPP)
 - Media Access Control


## OSI Layer

### Application Layer
Responsible for network applications (like HTTP / FTP) and their production of data to be transferred over the network.

### Presentation Layer
Translates data from the application layer into the format required to send data over the network as well as encrypt it.

### Session Layer


### Transport Layer

### Network Layer

### Data Link Layer

### Physical Layer


