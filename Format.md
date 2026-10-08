# 

## Objective
Develop a systematic approach to diagnosing network connectivity issues from a Linux endpoint by analyzing IP configuration, routing, DNS resolution, ICMP connectivity, TCP ports, sockets, and application-layer responses.


## Skills Demonstrated
-Network connectivity troubleshooting

-Linux network diagnostics

-IP configuration analysis

-Routing-table analysis

-Default gateway verification

-DNS troubleshooting

-ICMP connectivity testing

-TCP port testing

-Socket analysis

-HTTP/HTTPS troubleshooting

-Layered network troubleshooting

-Network issue isolation

-SOC-oriented network triage


## Tools used
Ubuntu Linux

Bash

VirtualBox

ip

ping

dig

nslookup

ss

nc

curl

traceroute


## Steps performed
-Verified endpoint network configuration

-Validated routing and default gateway configuration

-Tested local and external IP connectivity

-Tested DNS resolution separately from IP connectivity

-Examined active and listening sockets

-Tested TCP port connectivity

-Tested application-layer HTTP/HTTPS communication

-Traced traffic toward remote destinations

Used a structured troubleshooting methodology to isolate network issues.


## evidence (screenshots)

1) troubleshooting steps used on what Ive learned so far.

1. Interface
      ↓
2. IP configuration
      ↓
3. Routing
      ↓
4. Local/Gateway connectivity
      ↓
5. External IP connectivity
      ↓
6. DNS
      ↓
7. TCP/UDP service
      ↓
8. Application

2) Establishing a network baseline, used the ip addr command to identify:

Interface: enp0s3
IPv4 address: 10.0.2.15
CIDR: /24
Interface state: up

<img width="767" height="292" alt="image" src="https://github.com/user-attachments/assets/7ef14cd4-7fb1-4d6c-8846-2820810288a3" />

Then used the ip route command to identify:

Local subnet: 10.0.2.0/24
Default gateway: 10.0.2.2
Interface: enp0s3

<img width="600" height="62" alt="image" src="https://github.com/user-attachments/assets/85976772-f223-469e-9041-abaef976f78d" />

Then used the ip neigh command to identify my known neighbors specially the gateway.

<img width="550" height="92" alt="image" src="https://github.com/user-attachments/assets/9b1bbae8-6d8b-4aeb-961a-66971da69bba" />

2) Connectivity Ladder, I understand the connectivity ladder, I first pinged my the ip of my local network stack to test connectivity, then I pinged the main interface IP, then pigned my gateway and and then pinged and external ip, this was able to visualize the conenctivity ladder.

127.0.0.1

   ↓
   
Own IP

   ↓
   
Gateway

   ↓
   
External IP

3) DNS connectivity, Troubleshooting DNS, ran the dig youtube.com command, then the nslookup youtube.command, and resolvectl status command to identify the DNS server, resolve address and the DNS response.

<img width="662" height="610" alt="image" src="https://github.com/user-attachments/assets/d112a7da-738c-43f7-acbe-b372ca6f0e76" />

4) Testing TCP ports, used the netcat command: nc -vz youtube.com 443 command to test port 443 for the website.

<img width="601" height="36" alt="image" src="https://github.com/user-attachments/assets/52aad32c-444a-4f8b-9c86-b3ac48957c45" />

5) Testing sockets, used the ss -tuln and sudo ss -tl to check listening ports, protocols and local addresses.

<img width="740" height="456" alt="image" src="https://github.com/user-attachments/assets/35f11583-d776-48f3-88e6-8dbfffd8a991" />

## SOC relevance 
SOC analysts frequently need to determine whether failed or suspicious network activity is caused by malicious behavior, network configuration, DNS failure, firewall filtering, service availability, or application problems. Systematic network troubleshooting prevents incorrect conclusions during alert triage.

