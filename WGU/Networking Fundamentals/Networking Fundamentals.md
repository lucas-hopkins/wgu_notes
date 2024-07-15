
## Physical Layer

### Cable Types

The four most common types of transmission media are:
- Copper
- Coaxial
- Glass/fiber - 
- Air -infrared, satellite, wireless, or RF 

| Coaxial Type | Description                                                                 |
| ------------ | --------------------------------------------------------------------------- |
| RG-6         | Typically used for home audio, video, and TV transmission equipment         |
| RG-58        | Typically used for RF transmissions and antennae cabling to radio equipment |
| RG-58/U      | 10Base2 Ethernet, also known as Thinnet                                     |
| RG-59/U      | Closed circuit television (CCTV) transmission to monitors                   |
| RG-8U        | 10Base5 Ethernet, also known as Thicknet                                    |
| RG-60U       | HDTV and high-speed cable modems                                            |
- Crossover cable has a crossover pin configuration with the orange pair inserted where the green pair would normally be positioned on one end, creating a crossover connection. 
- Straight-through patch cables have each pin and colored wire connected to the exact same pin on the other end of the RJ-45 connector. 

### Fiber Optic
- Data transmitted by using pulses of light
- Transmission over great distances
- Highly secure

### Universal Serial Bus
- External serial bus connector
- Data transfer rate will depend on USB version - not the connector
- Type C
	- 24 pin connector
	- USB 3.1
		- SuperSpeed transfer mode
		- SuperSpeed+ transfer mode
	- USB 3.2
		- 10/20 Gbps for SuperSpeed and Superspeed+
### STP vs UTP 

- Both are cables with wires that are twisted together
- Shielded twisted pair uses a foil or mesh shield to reduce noise and crosstalk
	- Also require the use of an electrical ground


## Data Link Layer
- Media Access Control (MAC) - The MAC sublayer controls access to the media. This is where the Ethernet transceiver operates and interfaces with the Physical Layer. This sublayer listens to the network, and transmits or receives Ethernet frames onto the physical network. This listening is the carrier sense of __carrier sense multiple access with collision detection (CSMA/CD)__. 
- Logical Link Control (LLC) - The LLC sublayer controls linking logically. The LLC sublayer sits above the MAC sublayer and acts like a traffic cop, organizing the upper layer protocols into their MAC layer frame prior to transmission onto the network. Think of the LLC sublayer as the flow and error control traffic cop. It allows multipoint communications over a computer network.


## Network Types

### Wide Area Networks
- WANs connect systems over LARGE geographic area
- The Internet is the most common WAN
- __Border Routers__ - A border router sits between a WAN (usually the internet) and an internal network. Because the router is exposed to the WAN, it is subject to direct attack from from the outside. 
- __Internal Routers__ - Internal routers can also provide enhanced features to internal networks. They can help keep subnet traffic separate and provide dual protection of keeping undesired traffic out of and desired traffic in a subnet
- Routers can used __network address translation (NAT)__ and packet filtering to improve security. 

### Local Area Networks
- Provide network connectivity for computers that are in the same geo area and usually connected to each other with devices such as hubs and switches.
- Ethernet has become the most common LAN technology in use, and its standard defines how computers use MAC addresses to communicate with each other on the network.
- Primary LAN device is a __switch__
	- Connects several devices to the network.
	- Switches can perform intelligent filtering because they "know" the MAC address of the system connected to each port. When the receive a packet on the network, they look for the destination MAC address and send the packet to only the port where the destination system resides.
- Virtual LANs
	- A VLAN is created in the router and switch config setup, is a collection of logically related network devices that are viewed as a partitioned network segment. It gives administrators the ability to separate the network cabling  and can also be used to isolate logical groups of devices to reduce network traffic. 

#### Wireless Local Area Network (WLAN)
- Enables wireless network communication using wireless signals
- As opposed to traditional network cabling
#### Personal Area Network (PAN)
- Interconnecting devices focused on personal workspace
	- Laptops
	- Printers
	- Speakers
- Usually wireless, such as 
	- Bluetooth
	- Near-field communication (NFC)
- Keywork = sync

#### Metropolitan Area Network (MAN)
- Data network design used for a city or town
	- Similar to a LAN
- Formed by connecting multiple LANs
	- Making them typically larger than a LAN but smaller than a WAN
#### Campus Area Network (CAN)
- Proprietary local area network used to serve a University, Gov Agency, or Corporation
### Network Topology
- **Star Topology**
	- Each node is connected directly to a central hub or switch
- **Ring Topology**
	- Each node is responsible for passing information to and from each other (systems directly next to you)
	- Not used commonly, but may still be used in an ISP
- **Mesh Topology**
	- No central connection point that handles address tables
	- Every system is connected to every other system
- **Bus Topology**
	- Each system is connected to the main trunk and at each end there are termination points so that signals do not reflect back on themselves
	- Not effective as every devices receives every message
#### Wireless Topologies
- **Ad-hoc** - LAN that is built as devices as are added.
	- Each device can connect to the wireless device and to each other
- **Infrastructure Networks**
	- Use an AP
	- WLAN does not replace the LAN it just extends its functionality to wireless devices

## Network Deployments
- **On-Premise**
	- Within enterprise infrastructure
	- Physical access
	-  Software license requirements
- **Cloud**
	- Hosted third-party services
	- Off-site servers
	- Software-as-a-Service
- **Hybrid Cloud Model**
	- Combination of a public cloud infrastructure and a private cloud infrastructure
	- Benefits
		- Sharing data and deploying applications
		- Scalable services
		- Improved cost efficiencies
		- Reduced capital expenditures
		- Critical data remains behind firewall
	- Connects multiple infrastructure points together through a network to consolidate IT resources regardless of where they physically reside.
- __Multi-Cloud__
	- Similar to hybrid but removes the on-premise element
	- Combination of public or private cloud
	- Benefits
		- Able to scale up or scale down based on need
		- Automated workflows
		- Able to move resources as appropriate