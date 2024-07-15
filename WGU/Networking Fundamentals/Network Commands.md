
## Windows Commands

- __ipconfig__ - Returns network adapters along with their addresses
	- __/all__ - provides much more information about adapters including
		- DNS Servers
		- Dns Suffix
		- Adapter Information
	- __flushdns__ - will flush the DNS Resolver Cache
- __nslookup__ - returns the default 
	- typing in a FQDN will give you back the IP if it is able to resolve it
		- If it had to talk to another DNS server to find the answer, then it will return as a "Non-Authoritative Answer"
	-  Using __set type=ptr__ then entering an IP address will return the name
- __tracert__ - will trace all of the hops to get to a given website using ICMP
- __arp -a__ - mapping of IP to MAC of  devices on your LAN
- __netstat -an__ - returns all connections in numerical order
	
## Linux Commands
- __ip a__ - returns all network interfaces
- __ifconfig__ - returns interface information and also allows taking an interface down or back up.
-  __/etc/netplan/__ - yaml files used for configuring a network interface
- __/etc/resolve.conf__ - able to configure DNS servers
- __traceroute__ offers the same functionality as tracert
- __nslookup__ works the same way in Linux as in Windows
- __dig__ www.skillsoft.com - returns information about the DNS query for the given host (what type of record, how long it took, etc.)