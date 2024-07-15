
# OSI Model


- Layer 7: Application   - File, print, message, database, and application services
- Layer 6: Presentation - Data encryption, compression, and translation services
- Layer 5: Session - Dialog control
- Layer 4: Transport - End-to-end connection
- Layer 3: Network - Routing
- Layer 2: Data Link - Framing
- Layer 1: Physical - Physical Topology


## Application Layer

The application layer sends data from an application, like File Transfer Protocol (FTP), to the application layer of the destination host, and may control for data integrity and error recovery. The application layer comes into play only when it is apparent that access to the network will be needed soon. Take the case of your computer’s browser, e.g., Chrome or Firefox.
## Presentation Layer

By providing translation services, the presentation layer ensures that the data transmitted by one system’s application layer can be read and understood by the application layer on the system receiving that data. The OSI has protocol standards that define how standard data should be formatted. Tasks like data compression, decompression, encryption, and decryption are all associated with this layer. Some presentation layer standards may be involved in multimedia operations.
## Session Layer

The **session layer** is responsible for setting up, managing, and then tearing down communications sessions between networked computers.

A **simplex** transmission is a one-way, or unidirectional, communication. For example, a conventional radio station broadcast that you may be listening to is a simplex transmission because you can receive the signal on your radio, but you cannot transmit messages back to the radio station.


A **half-duplex** transmission is a communication in which you can both transmit and receive signals but only one way at a time. Think of the old-time walkie talkies in the movies where the people talking had to say “over” to indicate that they were going to stop talking and start listening.

A **full-duplex** transmission is a communication that allows you to speak and listen at the same time, for example, talking on a mobile phone.

## Transport Layer

The transport layer of a host sending data on the network uses a process of **segmentation**, **sequencing**, and **reassembly** to deliver application data to the transport layer of the host that is receiving the data.

TCP / UPD work at this layer

## Network Layer

The **network layer or Layer 3** manages logical device addressing, tracks the location of devices on the network, and determines the best way to move data from one network to another network. This means that the network layer must forward traffic between devices that are not part of the local area network (LAN).

IP works at this layer

Routers
## Data Link Layer

The data link layer or **Layer 2** provides the physical transmission of the data and handles error notification, network topology, and flow control.

The data link layer has two sublayers when using the **Ethernet** protocol: the **media access control (MAC) sublayer** and the **logical link control (LLC) sublayer**. The MAC sublayer defines how packets are placed on the media. Physical addressing is defined here. Each network interface has a unique MAC address, which enables delivery of frames to the destination host. The LLC is responsible for identifying network layer protocols and then encapsulating them. An LLC header tells the data link layer on the destination host what to do with a packet once a frame is received.

MAC works at this layer

Switches
## Physical Layer

The **physical layer** specifies the layout of the transmission **media**, otherwise known as its topology. A physical topology describes the way the cabling is physically laid out.
## TERMS

Session Layer

Responsible for setting up, managing, and then tearing down communications sessions between networked computers.

Simplex

Unidirectional; a one-way transmission.

Half Duplex

Providing communication in both directions, but only one direction at a time, not simultaneously.

Full Duplex

Describing a duplex system in which both parties can communicate with each other simultaneously.


# Coaxial & Twister Pair Cables

Coaxial cable contains a center conductor made of copper that is surrounded by a plastic jacket with a braided shield over it. A plastic such as polyvinyl chloride (PVC) or fluoroethylene propylene (FEP) covers this metal shield. The FEP-type covering is frequently referred to as a **plenum-rated** coating.

Utilized a physical bus topology, which you may recall is not as fault tolerant as a star-wired topology.


***NOTE***: Use plenum cables to help prevent fire spread

#term #cable-type Thin Ethernet, also referred to as **Thinnet** or 10Base2, is a thin coaxial cable. It is basically the same as thick coaxial cable, except that it is only about 5 mm, or 2/10 in., in diameter. Thin Ethernet coaxial cable is Radio Grade 58, or just RG-58.


#term #cable-type Twisted-pair cable is widely popular for building Ethernet LANs today, because it is lightweight, is easy to install, and supports the fault-tolerant physical star topology.

## Twisted Pair Categories

Cables are twisted to minimize crosstalk
### Category 1

Two twisted wire pairs (four wires). It is the oldest type and is only voice grade—it is not rated for data communication. People refer to it as **plain old telephone service (POTS)**.

### Category 3

Four twisted wire pairs (eight wires) with three twists per foot. This type can handle transmissions up to 16 MHz. It was popular in the mid-1980s for Ethernet of up to 10 Mbps
### Category 5

Four twisted wire pairs (eight wires), used for 100BaseTX (two-pair wiring) and rated at 100 MHz.
### Category 5e

Four twisted wire pairs (eight wires), recommended for 1000BaseT (four-pair wiring) and rated for 100 MHz but capable of handling the disturbance on each pair that is caused by transmitting across all four pairs at the same time—a feature that is needed for Gigabit Ethernet.

### Category 6

Category 6 became a standard in June 2002. You would usually use it as a **riser cable** to connect floors to each other. If you are installing a new network in a new building, there is no reason to use anything other than Category 6 UTP cabling as well as running **fiber-optic cable** between floors.

### Category 7

Although not recognized by the EIA/TIA, Category 7 cable, or Cat 7, allows 10 Gigabit Ethernet over 100 m of copper cabling. The cable contains four twisted copper wire pairs, just like the earlier standards. Cat 7 cables are double shielded to better mitigate crosstalk and EMI.


## UTP Connectors

#term Registered Jack (RJ)



# Fiber Optic Cable

Because fiber-optic cable transmits digital signals using light impulses rather than electricity, it is immune to **electromagnetic interference (EMI)** and **radio frequency interference (RFI)**.

Communication over a single strand of fiber is achieved by separating the transmission wavelength of the two devices, as depicted below. Think of it simply as, for example, blue light traveling in one direction and red light traveling in the other direction.

If your network runs are measured in miles, fiber optic is your cable of choice because copper cannot give you more than about 1,500 ft without electronics regenerating the signal. The standards limit UTP to a relatively short 328 ft.

Fiber also offers high security because it does not create a reliable magnetic field
## Single Mode Fiber

Single-mode fiber (SMF) is a very high-speed, long-distance medium that typically consists of a single strand of glass fiber that carries signals. Light-emitting diodes (LEDs) and lasers are the light sources used in SMF.

This type of fiber cable is employed to span really long distances, because it can transmit data 50 times farther than MMF and at a higher transmission rate.


## Multimode Fiber

Multimode fiber (MMF) also uses light to communicate a signal. However, the light is dispersed in numerous paths as it travels through the core and is reflected back.

Cladding is used to focus the light

MMF provides high bandwidth at high speeds over medium distances (up to about 3,000 ft)

MMF is available in a glass or plastic version that makes installation a lot easier and increases the installation’s flexibility.


## Fiber Optic Connectors

#term Angled Physical Contact (APC)
#term Ultraphysical Contact (UPC)

With the UPC, the light is reflected back down to the core of the fiber cable, which causes a loss of **dB** (decibel), called a return loss.

### ST Connector

ST uses a BNC attachment mechanism similar to Thinnet that makes connections and disconnections fairly easy.

### SC Connector

An SC APC connector is polished to an 8° angle, whereas an SC UPC connector is polished flat (no angle), which creates a difference in light reflection.

This is what I have

### FC Connector
Another type of connector is the FC connector or field assembly connector, also called the ferrule connector, which is not very popular. It is still used in telecommunications and measurement equipment with single-mode lasers, but the SC is more popular. FC connectors look identical to ST connectors.

### LC Connector

LC is a newer style of an SFF fiber-optic connector that is surpassing the MT-RJ. It is especially popular for use with Fiber Channel adapters (FCs) and is a standard used for fast storage area networks and Gigabit Ethernet adapters.
### SFF Connector

Small Form Factor Connector allows more fiber-optic terminations in the same amount of space than its standard-sized counterparts. The two most popular versions are the mechanical transfer registered jack (MT-RJ) designed by AMP and the Local Connector (LC) designed by Lucent.


## Transceivers 

#term A **transceiver** is a device composed of both a transmitter and a receiver, which are combined and share common circuitry and a single housing.

### SFP+

The small form-factor pluggable (SFP) is a compact, hot-pluggable optical module transceiver used for both telecommunications and data communications applications.
### QSFP

The Quad Small Form-Factor Pluggable (QSFP) is another compact, **hot-pluggable** transceiver used for data communications applications.

 It interfaces networking hardware, such as servers and switches, with a fiber-optic cable or active or passive electrical copper connection.


# Wiring & Cable Configurations

Some of the wiring standards available 
- T568A
- T568B
- Straight-through
- Crossover
- Rolled/rollover

### T568A vs.T568B

#imp The only difference between T568A and T568B is that the orange and green pairs are swapped on pins 1 and 2, and on pins 3 and 6.

If you are installing new cabling to typical cubicle or office workspaces, you need to use Cat 5e or Cat 6. **Voice-over IP (VoIP)** uses all eight pins, and it is really common to have voice and data on the same wire at the same time in modern networks, so it is best practice to connect all eight pins. Pins 4, 5, 7, and 8 are used in both standards.

This only leaves the wire pairs to connect to pins 1, 2, 3, and 6 for data. 

Remember, if we connect the orange-white, orange, green-white, and green wires to pins 1, 2, 3, and 6, respectively, on both sides of the cable, we are using the T568B standard and creating a straight-through cable that is commonly implemented as a **patch cable**.

If we switch from pin 1 to pin 3 and from pin 2 to pin 6 on one side only, we have created a **crossover cable**. Let us take a look.

### Straight-Through Cable

A **straight-through cable** is used to connect a host to a switch or hub or a router to a switch or hub. Four out of the eight wires are used in straight-through cable to connect 10 or 100 Mbps Ethernet devices.

### Crossover Cable

**Crossover cables** can be used to connect these devices:

1. Switch to switch
2. Hub to hub
3. Host to host
4. Hub to switch
5. Router direct to host


#imp If you are trying to match the straight-through and crossover cables with the T568A and T568B standard, here is how it would look:

            T568A+T568A = straight-through
            T568B+T568B = straight-through
            T568A+T568B = crossover

#imp #best_practice It is best practice to label a crossover cable as such so that no one tries to use it to connect a workstation to the network. If they do that, the workstation will not be able to communicate with the switch and the rest of the network because the transmit and receive pins are crossed.



# Ethernet Specifications

**Ethernet** is a contention-based media-access method that allows all hosts on a network to share the same bandwidth of a link.

#imp Ethernet uses both Layer 2 (Data Link) and Layer 1 (Physical) specifications

#term**Collision domain** is a particular area wherein one device sends a frame out on a network segment and every other device on that same physical network segment receives it. If two devices on one physical segment transmit at the same time, a **collision** occurs when each device’s signals interfere with another on the wire and forces the devices to retransmit later

Typically found in a **hub** environment where each host segment connects to a hub that represents only one collision domain and one broadcast domain.

#term A **broadcast** is a transmission address to all stations on a network. A **broadcast domain** refers to the set of all devices on a network segment that receive the broadcasts sent on that segment.

#term **Ethernet** networking uses **Carrier Sense Multiple Access with Collision Detection (CSMA/CD)**, a media access control method that helps devices share the bandwidth evenly without having two devices transmit at the same time on the network medium.

EXAMPLE
 When a collision occurs on an Ethernet LAN, the following things happen:
 - A jam signal informs all devices that a collision occurred.
 - The collision invokes a random back-off algorithm.
 - Each device on the Ethernet segment stops transmitting for a short time until the timers expire.
 - All hosts have equal priority to transmit after the timers have expired.


#term Broadband - allows us to send multiple frequencies of different signals down the same wire at the same time, which is called **frequency-division multiplexing**, and to send both analog and digital signals.

#term Baseband - is what all LANs use. For example, Ethernet uses only one digital signal at a time, and it requires all the available bandwidth. If multiple signals are sent from different hosts at the same time, we get collisions.

#term Bit Rate - **Bit rate** is a measure of the number of data bits (0s and 1s) transmitted in one second in either a digital or analog signal.

#term Baud Rate - One baud is one electronic state change per second, for example, from 0.2 volts to 3 volts or from binary 0 to 1.

#term Half-duplex Ethernet - One wire pair with a digital signal either transmitting or receiving.

	If a host hears a digital signal, it uses the CSMA/CD protocol to detect collisions and to permit retransmitting if a collision does occur. Half-duplex Ethernet, typically 10BaseT, is only about 30 to 40% efficient because a large 10BaseT network will usually provide only 3 Mbps to 4 Mbps at most.

#term Full-duplex Ethernet

	Full duplex uses a point-to-point connection between the transmitter of the sending device and the receiver of the receiving device, which in most cases is a switch. This means you do not need to worry about collisions because now you have multiple lanes.

When a full-duplex Ethernet port is powered on, it first connects to the remote end and then negotiates with the other end of the Fast Ethernet link. This is called an _auto-detect mechanism_. This mechanism first decides on the exchange capability, which means it checks to see if it can run at 10, 100, or even 1000 Mbps. It then checks to see if it can run full duplex, and if it cannot, it will run half-duplex instead. Hosts auto-detect by default both the speed (in Mbps) and the duplex type available, but you can manually set both the speed and duplex type on the network interface card (NIC)

### BINARY / HEX Conversion

Nibble is 4 bits
Byte is 8 (octet)

| Nibble Values | Byte Values |
| ---- | ---- |
| 8 4 2 1 | 128 64 32 16 8 4 2 1 |

 Looking at the table above, if we have set a 1 in each spot of our nibble, we then add up 8 + 4 + 2 + 1 to give us a maximum value of 15.

#### Hex
each hexadecimal character is one nibble and two hexadecimal characters together make a byte.

To figure out the binary value, first put the hexadecimal characters into two nibbles and then put them together into a byte. 6 = 0110 and A (which is 10 in decimal) = 1010, so the complete byte is 01101010.
#### Binary 
To convert from binary to hexadecimal, just take the byte and break it into nibbles.

#imp Say you have the binary number 01010101. First, break it into nibbles—0101 and 0101—with the value of each nibble being 5 because the 1 and 4 bits are set. 

This makes the hexadecimal answer 0x55. And in decimal format, the binary number is 01010101, which converts to 64 + 16 + 4 + 1 = 85.

### Ethernet Addressing

It uses the Media Access Control (MAC) address burned into an Ethernet **network interface card (NIC)**.

MAC address is 48 bit hex address with 24 bits being vendor assigned, and the remaining 24 being split between the Organizationally Unique Identifier (OUI)  and the Local/Global (L/G) bit / Individual/Group (I/G).
	The L/G is used to tell if the MAC address is the **burned-in-address (BIA)** or a MAC address that has been changed locally.

The Individual/Group (I/G) address bit is used to signify if the destination MAC address is a unicast or a multicast/broadcast Layer 2 address.
	If the bit is set to 0, then it is an Individual MAC address and is a unicast address. If the bit is set to 1, it is a Group address and is a multicast or broadcast address.

#term unicast - a transmission addressed to one station

#term multicast - a transmission address to multiple stations

#term broadcast - a transmission addressed to all stations






## Ethernet Frames

Fields in the 802.3 / Ethernet Frame Types

#term **Preamble** - The **preamble** is an alternating 1, 0 pattern that provides a clock at the start of each packet, which allows the receiving devices to clock the incoming bit stream.

#term **Start of Frame Delimiter (SOF)/Sync** -The SOF is 10101011, where the last pair of 1s allows the receiver to come into the alternating 1, 0 pattern somewhere in the middle and still sync up and detect the beginning of the data.

#term **Destination Address** - MAC address of the network interface card on the computer that the frame is being sent to. 

#term **Source Address** - 48-bit MAC address used to identify the transmitting device.

#term **Length or Type** - The **Ethernet II** (version 2) frame uses a Type field to identify the Network Layer protocol being carried in the data field of the frame. The original 802.3 used this field as Length, which indicated the size of the data field, but by itself it cannot identify the upper-layer routed protocol and must be used with a proprietary LAN protocol.

#term **Data** - This is a packet sent down to the Data Link Layer from the Network Layer. The size can vary from 64 to 1,500 bytes.

#term **Frame Check Sequence** - The **Frame Check Sequence (FCS)** is a field that is at the end of the frame and is used to store the CRC.



