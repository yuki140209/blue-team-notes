# Networking for Blue Team

## 1. Why Networking Matters in Blue Team
Networking is one of the most important foundations for Blue Team. Attackers move through networks, communicate with malicious servers, scan ports, send phishing links, and attempt unauthorized access over network protocols. Blue Team analysts must understand how devices communicate to detect suspicious activity.

If you do not understand networking, it becomes difficult to:
- Analyze traffic
- Investigate suspicious connections
- Understand logs
- Identify unusual behavior
- Use tools like Wireshark, SIEM, or firewall logs effectively

---

## 2. What is a Network?
A network is a group of devices connected to each other so they can communicate and share data.

Examples of devices on a network:
- Laptops
- Servers
- Mobile phones
- Routers
- Printers
- Firewalls

---

## 3. IP Address
An **IP address** identifies a device on a network.

Example:
- `192.168.1.10`

It helps devices know **where to send data**.

### Types of IP addresses

#### Private IP
Used inside internal networks such as home Wi-Fi or office networks.
Examples:
- `192.168.x.x`
- `10.x.x.x`
- `172.16.x.x – 172.31.x.x`

#### Public IP
Used on the internet and is visible externally.

### Why IPs matter in Blue Team
Blue Team analysts check IP addresses to:
- Identify the source of suspicious traffic
- Find attacker IPs
- Detect unusual login locations
- Investigate connections to malicious servers

---

## 4. MAC Address
A **MAC address** is a unique hardware address assigned to a network interface card (NIC).

Example:
- `00:1A:2B:3C:4D:5E`

### Difference between IP and MAC
- **IP address** → logical address used for communication across networks
- **MAC address** → physical hardware address used inside local networks

---

## 5. DNS (Domain Name System)
DNS translates human-readable domain names into IP addresses.

Example:
- You type `google.com`
- DNS returns an IP address for Google’s server

### Why DNS matters in Blue Team
Attackers often use:
- malicious domains
- phishing domains
- command-and-control (C2) domains

Blue Team can analyze DNS requests to detect suspicious domains.

---

## 6. DHCP (Dynamic Host Configuration Protocol)
DHCP automatically assigns IP addresses to devices on a network.

Instead of manually assigning an IP to every device, DHCP gives devices an address automatically.

### Why DHCP matters
In investigations, DHCP logs can help identify:
- which device received which IP
- when a device joined the network

---

## 7. Port
A **port** is a numbered communication endpoint used by services and applications.

Example:
- A web server may use port **80** or **443**
- SSH commonly uses port **22**

Ports help the system know **which application or service should receive the traffic**.

---

## 8. Protocol
A protocol is a set of rules for communication between devices.

Examples:
- HTTP
- HTTPS
- DNS
- FTP
- SSH
- TCP
- UDP

Blue Team must know protocols because logs and alerts often mention them.

---

## 9. TCP vs UDP

## TCP (Transmission Control Protocol)
TCP is a **connection-oriented** protocol. It is reliable and ensures data arrives correctly.

### Features of TCP
- Reliable
- Ordered delivery
- Error checking
- Used when accuracy matters

### Common TCP uses
- Web browsing (HTTP/HTTPS)
- SSH
- Email
- File transfer

---

## UDP (User Datagram Protocol)
UDP is **connectionless** and faster, but less reliable than TCP.

### Features of UDP
- Faster
- No guaranteed delivery
- No connection setup
- Used when speed matters more than reliability

### Common UDP uses
- DNS queries
- Video streaming
- Online gaming
- Voice calls

---

## 10. Common Ports Blue Team Should Know

| Port | Protocol / Service | Use |
|---|---|---|
| 20/21 | FTP | File transfer |
| 22 | SSH | Secure remote login |
| 23 | Telnet | Insecure remote login |
| 25 | SMTP | Sending email |
| 53 | DNS | Domain name resolution |
| 67/68 | DHCP | IP address assignment |
| 80 | HTTP | Web traffic |
| 110 | POP3 | Email retrieval |
| 123 | NTP | Time synchronization |
| 143 | IMAP | Email retrieval |
| 161/162 | SNMP | Network monitoring |
| 389 | LDAP | Directory services |
| 443 | HTTPS | Secure web traffic |
| 445 | SMB | File sharing in Windows |
| 3389 | RDP | Remote Desktop Protocol |

### Why these ports matter
If you see unexpected traffic on certain ports, it may indicate:
- scanning
- brute-force attempts
- lateral movement
- unauthorized remote access
- malware communication

---

## 11. HTTP vs HTTPS

## HTTP
HTTP is used to transfer web content between browser and server.
- Default port: **80**
- Not encrypted

## HTTPS
HTTPS is the secure version of HTTP.
- Default port: **443**
- Uses encryption (TLS/SSL)

### Blue Team importance
Sensitive data should use HTTPS, not plain HTTP. Suspicious HTTP traffic can sometimes expose malware communication or insecure web activity.

---

## 12. FTP, SSH, and Telnet

### FTP
Used for file transfer. Traditional FTP is not secure because credentials may be sent in plain text.

### SSH
Used for secure remote login and remote command execution.
- Port 22
- Important for server administration
- Attackers may try brute-force attacks against SSH

### Telnet
Used for remote login but is insecure because it does not encrypt traffic.
- Port 23
- Generally avoided in secure environments

---

## 13. What is a Packet?
A packet is a small unit of data sent across a network. When data travels over a network, it is broken into packets.

Blue Team analysts may inspect packets to understand:
- source and destination
- protocol used
- suspicious payloads
- malware communication patterns

Tools like **Wireshark** help analyze packets.

---

## 14. OSI Model
The OSI model is a conceptual framework that explains how data moves across a network.

### 7 Layers of OSI Model
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

---

## 15. Simple Understanding of OSI Layers

### Layer 1 – Physical
Deals with cables, electrical signals, hardware transmission.

### Layer 2 – Data Link
Deals with MAC addresses and communication within the local network.

### Layer 3 – Network
Deals with IP addresses and routing.

### Layer 4 – Transport
Deals with TCP and UDP.

### Layer 7 – Application
Deals with protocols like HTTP, HTTPS, DNS, SMTP.

You do not need to memorize every detail immediately, but you should know the basic purpose of each major layer.

---

## 16. Firewall
A firewall controls network traffic based on rules. It can allow or block traffic.

### Why firewalls matter in Blue Team
Firewall logs can show:
- blocked connections
- suspicious outbound traffic
- repeated attempts to access services
- communication with suspicious IPs

---

## 17. VPN (Virtual Private Network)
A VPN creates an encrypted connection between a user and a network.

### Blue Team relevance
VPN logs are useful for:
- tracking remote user access
- checking login times
- investigating unusual access attempts
- identifying account misuse

---

## 18. Network Traffic Analysis in Blue Team
Blue Team often checks:
- source IP
- destination IP
- port numbers
- protocol
- amount of traffic
- unusual destinations
- failed connections
- repeated connection attempts

---

## 19. Common Suspicious Network Signs

### Repeated failed connections
May indicate scanning or brute-force attempts.

### Connections to known malicious IPs or domains
May indicate malware or command-and-control communication.

### Unusual outbound traffic
A compromised system may send data to an attacker.

### Large data transfers at odd times
May indicate data exfiltration.

### Traffic to rare ports
Could suggest unauthorized tools or malicious activity.

### Internal device contacting many systems quickly
May indicate lateral movement or scanning.

---

## 20. Networking Terms Blue Team Should Know

### Source IP
The IP address that sent the traffic.

### Destination IP
The IP address receiving the traffic.

### Source Port
The sender’s port.

### Destination Port
The target service’s port.

### Inbound Traffic
Traffic coming into a network or system.

### Outbound Traffic
Traffic leaving a network or system.

### Latency
Delay in communication.

### Bandwidth
Amount of data that can be transmitted over a connection.

---

## 21. Why Networking Knowledge Helps in SIEM and Logs
Security logs often contain:
- source IP
- destination IP
- destination port
- protocol
- hostname
- DNS request
- connection status

Without networking basics, these logs are difficult to interpret.

---

## 22. Quick Revision Notes
- IP address identifies a device on a network
- MAC address identifies network hardware
- DNS converts domain names into IP addresses
- DHCP assigns IP addresses automatically
- Ports identify services like HTTP, SSH, and DNS
- TCP is reliable and connection-oriented
- UDP is faster and connectionless
- HTTP uses port 80, HTTPS uses 443
- SSH uses port 22, RDP uses 3389, DNS uses 53
- Firewall logs are very useful for Blue Team investigations
- Suspicious traffic can include scanning, brute force, unusual outbound traffic, and malicious DNS requests

---

## 23. Interview / Viva Questions
1. Why is networking important for Blue Team?
2. What is the difference between IP and MAC address?
3. What is DNS and why is it important in security?
4. What does DHCP do?
5. What is the difference between TCP and UDP?
6. What are some important ports a SOC analyst should know?
7. What is the difference between HTTP and HTTPS?
8. What kind of suspicious activity can be found in network traffic?
9. What is the role of a firewall?
10. Why are DNS logs useful in investigations?

---

## 24. Short Summary
Networking is a core skill for Blue Team because security incidents often involve IP addresses, ports, protocols, DNS requests, remote access, and suspicious network connections. A Blue Team analyst must understand how devices communicate in order to analyze logs, investigate alerts, and detect malicious behavior.
