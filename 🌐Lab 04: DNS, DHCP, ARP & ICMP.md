# 🌐 Networking Fundamentals — Lab 04: DNS, DHCP, ARP & ICMP

## Objectives
Develop practical knowledge of core network protocols used for name resolution, dynamic host configuration, local network address resolution, and connectivity diagnostics. Perform hands-on DNS, DHCP, ARP, and ICMP analysis from a Linux endpoint and relate protocol behavior to common SOC investigations.

## Skills Demonstrated
-DNS query and resolution analysis

-DNS record identification

-DHCP configuration analysis

-ARP/neighbor-table analysis

-IP-to-MAC address mapping

-ICMP connectivity testing

-Basic network troubleshooting

-DNS server identification

-Default gateway identification

-Network protocol identification

-Interpretation of common network indicators

-Basic SOC network triage

## Tools used
-Bash Commands: 

dig

nslookup

resolvectl

ip neigh

ping

ip addr

ip route

## Steps performed
-Queried DNS records and analyzed DNS responses

-Identified the DNS resolver used by a Linux endpoint

-Examined DHCP-assigned network configuration

-Identified the endpoint's IPv4 address, subnet, and default gateway

-Examined the local ARP/neighbor cache

-Correlated IPv4 addresses with MAC addresses

-Generated local traffic to populate neighbor information

-Tested local and external connectivity using ICMP

-Compared successful and unsuccessful connectivity tests

-Applied DNS, DHCP, ARP, and ICMP knowledge to simulated SOC scenarios



## evidence (screenshots)

1) DNS, Domain name system, allows you to change human readeble domain name into its associtaed IP.

Common DNS flags:


| `A` | Hostname → IPv4 |
| `AAAA` | Hostname → IPv6 |
| `CNAME` | Alias to another hostname |
| `MX` | Mail server |
| `NS` | Authoritative name server |
| `TXT` | Text information/policies |

Common ports for DNS: UDP/53 , TCP/53

Used the nslookup command to be able to query the DNS server for youtube.com, here I was able to view the following information:

<img width="322" height="392" alt="image" src="https://github.com/user-attachments/assets/97a6a8a3-3e11-42d9-9c13-5dce51892511" />

<img width="590" height="322" alt="image" src="https://github.com/user-attachments/assets/97551be5-9405-4793-affa-35613851fe20" />


QUESTION SECTION: who made the query
ANSWER SECTION: response to the query
SERVER: the server from which the request came from.
Query time: and how long the query request took.

Used the resolvectl status command to see what is the IP address of the DNS resolver.

<img width="642" height="227" alt="image" src="https://github.com/user-attachments/assets/358d459d-ab37-43e7-9595-fc9173305313" />

In this case the IP is: 10.0.0.1

2) DHCP, DynamiC host configuration protocol, automically configures each host computer with its, IP, Default Gateway, DNS and subnet mask.

It uses a the DORA sequence Discover, Offer, Request, Acknowledge.

Common ports:

UDP 67 → Server

UDP 68 → Client

Did a an examination of the network configuration by using the ip a command to identify the interface: enp0s3, IPv4: 10.0.2.15, and CIDR (subnet mask): /24, then used the IP route command to determine the default gateway:10.0.2.2 and the local subnet:10.0.2.0/24 and finally used the resolvectl command to verify the DNS resolver IP: 10.0.0.1.

<img width="757" height="537" alt="image" src="https://github.com/user-attachments/assets/6f26e6b9-f1f2-4387-897d-289b761b4c24" />

3) ARP, Address Resolution Protocol. it is used in Ipv4 to associated MAC addresses to IPv4 addresses in the local link

Used the ip neigh command to view the MAC address of the default gateway.

<img width="565" height="75" alt="image" src="https://github.com/user-attachments/assets/8aa16fd5-729f-4e31-81c4-c79f0b53a331" />

Used the ping command to ping the gateway and after than the ip neigh command to see neighbor information, I was able to identify that the status changed from stale to reachable and see the neighbors MAC address.

<img width="551" height="75" alt="image" src="https://github.com/user-attachments/assets/e282ecac-e614-4a1d-bb29-25b379544152" />


4) ICMP Internet Control Message Protocol, it is used for network control, diagnostics and error reporting functions. for example the ping command use this protocol. which used the ICMP echo request and ICMP echo reply functionanily specfically.

I tested the Loopback connectivity by pinging the local interface at 127.0.0.1 and was able to determine that there is 0% packet loss.

<img width="520" height="185" alt="image" src="https://github.com/user-attachments/assets/0d2c4223-974b-49e9-8197-80ace56ab19a" />


5) DNS vs. Connectivity troubleshooting.

If you ping the IP of a domain directly instead of using the Human readable name for that domain and it works but then you ping the Human readable name and it does not work, that will let you know that there is an issue with the DNS.

## lessons learned

I learned what DNS, DHCP, ICMP and ARP and how they work and why they are important in a SOC context for investigations and diagnostics.

## SOC relevance 
DNS, DHCP, ARP, and ICMP provide important context during security investigations. SOC analysts use DNS activity to investigate suspicious domains, DHCP information to associate network configuration with endpoints, ARP information to understand local Layer-2 relationships, and ICMP activity to troubleshoot connectivity or investigate unusual network behavior.
