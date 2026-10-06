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

1- 

2- 

3- 

4-

5- 

6- 

7- 

8- 


## lessons learned




## SOC relevance 
DNS, DHCP, ARP, and ICMP provide important context during security investigations. SOC analysts use DNS activity to investigate suspicious domains, DHCP information to associate network configuration with endpoints, ARP information to understand local Layer-2 relationships, and ICMP activity to troubleshoot connectivity or investigate unusual network behavior.
