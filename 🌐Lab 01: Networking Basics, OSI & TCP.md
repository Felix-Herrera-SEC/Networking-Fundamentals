# 🌐Lab 01: Networking Basics, OSI & TCP/IP

## Objectives

Develop a practical understanding of the OSI and TCP/IP networking models while identifying network interfaces, IP addresses, MAC addresses, routing information, and network connectivity on a Linux endpoint.

Interpret basic information contained in a network security alert

## Skills demostrated 

-OSI and TCP/IP networking fundamentals

-Network interface identification

-address identification

-MAC address identification

-Basic routing-table interpretation

-Default gateway identification

-ICMP connectivity testing

-Basic interpretation of network security alerts

## Tools used

-Bash Commands:

hostname

hostname -I

ip addr

ip link

ip route

ping

## Steps performed 

Identified the endpoint's hostname, network interface, IPv4 address, MAC address, and default gateway; examined the local routing table; tested remote IP connectivity using ICMP; and mapped observed network information to the corresponding OSI layers.

## evidence (screenshots)

1- Reviewed the OSI model and the TCP/IP model to have the layers with are going to be working with top of mind.

OSI Model:

<img width="560" height="456" alt="image" src="https://github.com/user-attachments/assets/1f2301a0-1ff3-43b1-a5c1-9b1ae6274a77" />

TCP/IP Model

+---------------------------------------------------------+

| 4. Application Layer  (HTTP, SSH, DNS, FTP, SMTP)      |

+---------------------------------------------------------+

| 3. Transport Layer    (TCP, UDP)                        |

+---------------------------------------------------------+

| 2. Internet Layer     (IP, ICMP, ARP)                   |

+---------------------------------------------------------+

| 1. Network Access     (Ethernet, Wi-Fi, MAC addresses)  |

+---------------------------------------------------------+

Here is the TCP/IP model mapped to the OSI model.

| OSI Model (7 Layers) | TCP/IP Model (4 Layers) | Core Functions & Protocols |
| :--- | :--- | :--- |
| **7. Application** | **Application Layer** | High-level protocols, network services, user interfaces (HTTP, HTTPS, SSH, DNS, FTP, SMTP) |
| **6. Presentation** | | Data formatting, encryption/decryption, compression (TLS/SSL, JPEG, ASCII) |
| **5. Session** | | Establishing, managing, and terminating communication sessions (RPC, NetBIOS) |
| **4. Transport** | **Transport Layer** | End-to-end communication, flow control, error checking (TCP, UDP) |
| **3. Network** | **Internet Layer** | Logical addressing, routing across networks (IP, ICMP, ARP) |
| **2. Data Link** | **Network Access Layer** | Hardware addressing, framing, media access control (Ethernet, Wi-Fi, MAC addresses) |
| **1. Physical** | | Physical transmission medium, electrical/optical signals, cables, network interface cards (NICs) |

---

Key Mapping Differences

* **Upper Layers (OSI 5, 6, 7 → TCP/IP Application):**
  * The OSI model splits software interaction into Application, Presentation, and Session.
  * The TCP/IP model consolidates all three into a single **Application Layer**.

* **Lower Layers (OSI 1, 2 → TCP/IP Network Access):**
  * The OSI model separates physical hardware from framing/addressing.
  * The TCP/IP model combines both into the **Network Access Layer**.


2- Understanding that encapsulation is the process in which data travels through the networking stack.


3- On my ubuntu terminal used the hostname command to identiy for the host, then used the hostname -I to identify the ip associated with the host, after I used the ip addr command to view information on the network interfaces.

<img width="770" height="367" alt="image" src="https://github.com/user-attachments/assets/99446a90-c7fb-4ef8-8fae-2fbef3e9d08f" />

From this I was able to identify the interface: enp0s3, the IPv4: 10.0.2.15, CIDR: /24

This belogs to the layer 3 of the OSI model Network.

4- Used the ip link command to viw the MAC address of the main interface, in this case: link/ether 08:00:27:b4:36:61.

<img width="777" height="131" alt="image" src="https://github.com/user-attachments/assets/8740118e-35ea-4a41-a5f3-b672445fa6f8" />

This belongs to the layer 2 of the OSI model.


5- Used the ip route command to view the routing table and was able to establish that the default gateway ip is: 10.0.2.2 and the interface as: 10.0.2.2

<img width="586" height="55" alt="image" src="https://github.com/user-attachments/assets/d7d19173-174d-44b0-92bd-3932a98032a3" />

6- Used the ping command to test network connectivity and was able to verify all the packets sent where recieved.

<img width="445" height="117" alt="image" src="https://github.com/user-attachments/assets/521103d2-9686-44e4-b9fc-e9a7f6bf16e9" />

7- Used all the commands together and was able to indentify the following information:

-Host name (which enpoint)? Ubuntu
-Network interface (which interface is being used)? enp0s3
-IPv4 address: 10.0.2.15
-MAC address: link/ether 08:00:27:b4:36:61.
-Default gateway: 10.0.2.2

<img width="777" height="545" alt="image" src="https://github.com/user-attachments/assets/bf96dd72-86a1-4be5-9836-b5fd9e57c895" />

## lessons learned

Understood how the OSI model and the TCP/IP model map to each other, also how to determine hostname and the ip associated with is using the hostname and hostname -I commands, how to determine the main interface using the ip a and the ip route commands, and how to identify the IPv4 in an interface, the mac adddress of the interface using the ip link command and idenity the default gateway using the routing table.

## SOC relevance 

Understanding network addressing, protocols, and communication layers provides the foundation for analyzing security alerts containing source and destination IP addresses, ports, protocols, and network connection information.
