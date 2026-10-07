# 🌐 Networking Fundamentals — Lab 05: Application-Layer Protocols & Services

## Objective
Develop practical knowledge of common application-layer network protocols and services, including HTTP/HTTPS, SSH, FTP, SMTP, and SMB. Identify their typical ports, interact with selected services from Linux, and analyze how application protocols appear during SOC investigations.
## Skills Demonstrated
Application-layer protocol identification

Service-to-port mapping

HTTP request/response analysis

HTTP header inspection

HTTPS/TLS awareness

SSH service identification

FTP architecture and port recognition

SMTP/email protocol fundamentals

SMB service identification

Linux network service inspection

Basic client/server troubleshooting

SOC-oriented service analysis

## Tools used
Ubuntu Linux

Bash

VirtualBox

TryHackMe

curl

ssh

ss

nc

dig

## Steps performed
-Identified common application protocols and their standard ports

-Generated and inspected HTTP/HTTPS requests

-Examined HTTP response headers and status codes

-Distinguished HTTP from HTTPS

-Examined SSH client behavior

-Reviewed FTP control/data concepts

-Identified SMTP and related email protocols

-Examined SMB's role in Windows environments

-Inspected Linux network sockets

-Analyzed simulated SOC alerts involving common services

## evidence (screenshots)

1)Application layer protocols, protocols that function in the application layer (7) of the OSI model, they provide network functionality directly used by applications and services.

Common application layer protocols, purpose and common ports:

| HTTP | Web | TCP 80 |

| HTTPS | Encrypted web | TCP 443 |

| SSH | Secure remote access | TCP 22 |

| FTP | File transfer | TCP 20/21 |

| SMTP | Email transmission | TCP 25 |

| POP3 | Retrieve email | TCP 110 |

| IMAP | Email access | TCP 143 |

| SMB | Windows file/resource sharing | TCP 445 |

2)HTTP, hypertext transfer protocol, is one of the fundamentl protocols used by the web.

HTTOP methods: GET,POST,PUT,DELETE.

Get: Request information/resources.
POST: Commonly sends data to the server.

HTTP status codes: 

1xx → Informational

2xx → Success

3xx → Redirection

4xx → Client error

5xx → Server error

Common examples:

200 → OK

301 → Moved Permanently

302 → Found / redirect

400 → Bad Request

401 → Unauthorized

403 → Forbidden

404 → Not Found

500 → Internal Server Error

503 → Service Unavailable

3) Genrated an HTTP request by using the curl http://youtube.com comannd, then used the curl -I command to request the reponse headers, procotol, version, server response and the status code.

<img width="510" height="252" alt="image" src="https://github.com/user-attachments/assets/1f1e7eac-b796-4f24-9805-be0c4afff721" />

Protocol/version: http 1.1

Status code: 301

Headers: content type, cache control, pgrama, expires, dates etc

Server response: HTTP/1.1 301 Moved permanently.

4) HTTPS, http protected using TLS (transport layer securty)

you can observer the following information inside wireshark uhen obesrving HTTPS:

Source IP

Destination IP

Ports

Timing

Connection volume

TLS information.

4)SSH, Secure Shell, commonly uses TCP/22

its importat cause it may represent:

Legitimate administration

OR

Unauthorized remote access

OR

Brute-force attempts

OR

Compromised credentials

OR

Lateral movement

Examined my ssh client by using the ssh -v command, then used ssh command to view the usage and the ss -ltn command to view if there is any active connections on port 22.

<img width="737" height="482" alt="image" src="https://github.com/user-attachments/assets/effe87f1-35a3-4c7e-a296-5813bf812c5d" />

5) FTP, file transfer protocol.

Traditionally uses the following ports:

TCP/21 → control connection

TCP/20 → traditionally associated with active-mode data

raditional FTP does not inherently protect credentials and data with encryption.

Secure alternatives include technologies such as: SFTP which is the SSH file transfer protocol through SSH.

Typically: SFTP → TCP/22

6) SMTP, POP3 and IMAP.

SMTP, simple mail transfer protocol, it helps send/transfer emails, usually through port TCP/25

POP3, Post Office Protocol version 3, helps retrieve emails, usually through port TCP/110

IMAP, Internet Message Access Protocol. Used to access/manage email stored on a mail server. usually through port TCP/143

7) SMB, server message block, common port: TCP/445, its supports things like:

File sharing

Printer sharing

Shared folders

Network resources

Heavyly associated with windows enviroments.

8) I examined my network services by sudo ss -tulnp command and find the folling information:

<img width="727" height="512" alt="image" src="https://github.com/user-attachments/assets/52d7cacf-07b0-44d3-9261-97e8485afa96" />

SSH

TCP or UDP? TCP

Listening or active? Listening

Which local port? 22

Which process? SSH

Do I recognize the service? Yes




## lessons learned

Learned about application layer protocols, how they work, which ones are common and their ports, and how to invstagate and find this details inside the linux terminal.


## SOC relevance 

SOC analysts routinely investigate alerts involving web traffic, remote administration, email, file transfers, and Windows file sharing. Recognizing common application protocols and ports helps analysts determine the likely purpose of a connection, identify unusual service usage, and decide what additional endpoint, network, or authentication evidence should be investigated.
