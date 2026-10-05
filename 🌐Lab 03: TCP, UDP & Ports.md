# 🌐 Networking Fundamentals — Lab 03: TCP, UDP & Ports

## Objectives

Develop practical knowledge of TCP and UDP communications, network ports, connection establishment, and common application protocols while learning to interpret source/destination IP addresses, ports, and transport protocols from a security-analysis perspective.

## Skills Demonstrated

-TCP and UDP protocol identification

-Source and destination port interpretation

-Common network service port identification

-TCP three-way handshake analysis

-TCP flag interpretation

-Active connection identification

-Listening-port identification

-Socket analysis on Linux

-Client/server communication analysis

-Basic network connection triage

-Recognition of unusual ports and services in security telemetry

## Tools used

-Bash Commands:

ss
ss -t
ss -u
ss -l
ss -tuln
ss -tunap
curl
nc
ip addr

## Steps performed

-Compared TCP and UDP communication characteristics

-Identified common TCP/UDP service ports

-Examined listening TCP and UDP sockets on a Linux endpoint

-Identified source and destination ports in active connections

-Generated network connections and observed their socket information

-Created a controlled TCP client/server connection using Netcat

-Identified TCP connection states

-Analyzed the TCP three-way handshake concept

-Interpreted simulated SOC network alerts containing IP, port, and protocol information

## evidence (screenshots)

1) Learned what TCP is, (transmission control Protcol), Connection oriented, before application data is exchanged, TCP establishes a connection between the two endpoints.

It provides features such as:

Reliable delivery

Ordered delivery

Sequence numbers

Acknowledgments

Retransmission of lost data

Connection establishment

Connection termination

Basically it establishes a connection and keeps track of whether the data arrieves correctly.

Common application/protocols that typically use TCP include: HTTP, HTTPS, SSH, FTP, SMTP.

2) Learned about UDP, User Datagram Protocol, UDP is connectionless, it does not establish TCP style connection before sending data.

UDP has less protocol overhead but dosent itself provide TCPs realiability.

basically it send dattagram without first establishing a TCP-style connection.

UDP is commonly associated with: DNS, DHCP, VoIP, Streamng, Gaming.

Simplified mental model:

TCP: Did you recieve it? yes, did you recieve the next one? yes
UDP: Here you go, here you go, here you go.


3) Netwroking ports, TCP and UDP port numbers range from 0-65535, they allow network communicatoin to be asociated with particular application endpoints.

For example:

192.168.1.50:22 means this is IP is associated with port 22

4) The TCP 3 way handshake, SYN (I want to establish a TCP connection), SYN-ACK (I recieved your request and Im ready), ACK (Acknowledged)

SYN - SYN/ACK - ACK

TCP flags: 

SYN (establish connection)

ACK (Acknowledge received data/control)

FIN (Gracefully terminate connection)

RST (Reset connection)

PSH (Request prompt delivery to application)

TCP connection states: LISTEN, ESTAB, TIME-WAIT, SYN-SENT, SYN-RECV, CLOSE-WAIT

LISTEN: A local socket is waiting for incoming connections

for example: 0.0.0.0:22 might indicate that an SSH service listening on TCP port 22

ESTAB: An active TCP connection exists.

5) Used the ss -tuln command to open all active network sockets, picked one of the sockets and was able to identify the following information:

<img width="522" height="20" alt="image" src="https://github.com/user-attachments/assets/bcd00b1b-83e6-4a35-ae13-ce7e4c876c43" />

Transport protocol: TCP

Local IP: 127.0.0.54

Port: 53

Connection state: Listening


6) Used the ss -tlp command to view all network sockets and was able to see all processes, the protcol they are using and the port associated with the process.

<img width="361" height="35" alt="image" src="https://github.com/user-attachments/assets/fcce7882-481f-4836-b72d-1ba37b551544" />

7) Created my own TCP server inside the VM, started by using the nc -lv command 4444 I told NetCat to listen to port 4444 then opened a new terminal and use the ss -tln | grep :4444 comand to view the specific activty.

<img width="447" height="131" alt="image" src="https://github.com/user-attachments/assets/8dad421b-9b63-4cb0-af4c-c2bfd49a6bd3" />

The from the second terminal using the nc 127.0.0.1 4444 command I established the connection, then I typed a srtring of text in the client and recieved it in the other terminal.

<img width="442" height="182" alt="image" src="https://github.com/user-attachments/assets/d43f2eb2-a312-4ee4-9137-4541d61cd849" />

Then used the ss -tn command to view the state of the connection, the IP associated with it and the port through which they where communicating.

<img width="830" height="77" alt="image" src="https://github.com/user-attachments/assets/e1117c9a-c05a-488f-bcbf-53c4583450fb" />

Source IP: 127.0.0.1

Source port: 4444

Destination IP: 127.0.0.1

Destionation port: 45152 (ephemeral)

## lessons learned

Learned about TCP and UDP, and how they are the most common transport protcols used for most ports, learned about common pors and how to check network sockets and ports inside the linuxx terminal, and how to make a tcp server using netcat.


## SOC relevance 

Understanding TCP, UDP, ports, and connection states enables SOC analysts to interpret firewall, IDS/IPS, SIEM, EDR, and packet-capture data. Analysts use this information to identify communicating systems, determine which services are involved, recognize unusual network behavior, and investigate suspicious connections.
