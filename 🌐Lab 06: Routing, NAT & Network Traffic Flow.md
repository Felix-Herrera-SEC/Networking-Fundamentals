# 🌐 Networking Fundamentals — Lab 06: Routing, NAT & Network Traffic Flow

## Objective
Develop practical understanding of IP routing, default gateways, routing tables, NAT, and end-to-end network traffic flow. Analyze how a Linux endpoint determines where packets should be sent and trace traffic from a private network toward external destinations.


## Skills Demonstrated
- Linux routing-table analysis

- Default gateway identification
  
- Route selection fundamentals
  
- Local vs. remote network determination

- Next-hop identification

- Network Address Translation (NAT) fundamentals
  
- Private vs. public IP analysis
  
- Packet-path analysis
  
- Hop-by-hop route discovery

- Basic network troubleshooting

- Linux network-interface analysis

- SOC-oriented network traffic interpretation

## Tools used
Ubuntu Linux

Bash

VirtualBox

TryHackMe

ip addr

ip route

ip neigh

ping

traceroute

curl


## Steps performed
Identified the endpoint's IPv4 address and subnet

Examined the Linux routing table

Identified the default gateway

Distinguished local-subnet traffic from remote traffic

Determined next-hop routing decisions

Examined gateway neighbor information

Traced traffic toward an external destination

Compared private and public addressing

Studied NAT/PAT behavior

Reconstructed an end-to-end packet path

Applied routing knowledge to simulated SOC network events

## evidence (screenshots)

1) Routing, is the process of determining where packets should be sent to reach their destination. used ip route to view the routing table inside ubuntu.
   
<img width="577" height="57" alt="image" src="https://github.com/user-attachments/assets/366515f4-ad44-4901-bf38-705a1b2591b1" />

here I was able to see my default gateway, local subnet and interface.

2) What is next-hop?

A router doesn't necessarily know the entire physical journey of a packet.
It needs to know where to send it next.

Routing + ARP, the router needs to know the MAC address for the gateway before sensing informaiton.

Route selction inside linux

<img width="442" height="62" alt="image" src="https://github.com/user-attachments/assets/99f7b9b3-d588-4bef-930a-f50ece159a21" />

Longest prefix matching, routing will always choose the more specific route, the one with the highest prefix

3) NAT , Network address translation.

NAT device translates addressing information as traffic crosses the boundary.

How can multiple devices share one public IP simultaneously?
Ports can help distinguish translations.
You'll commonly hear this described as PAT — Port Address Translation, or NAPT.
For example:

4) comparing my private ip and public IP.

<img width="385" height="72" alt="image" src="https://github.com/user-attachments/assets/c122390c-309c-4122-9abf-eef340b5c04b" />

NAT converts makes it so my private IP and public facing IP are different by route external traffic through my local.

5) using traceroute command to understand routing.

<img width="545" height="571" alt="image" src="https://github.com/user-attachments/assets/9d910af8-95bf-4778-b85d-648bdd228e50" />

## lessons learned

SAME SUBNET
Host
 ↓
Destination directly reachable on local link


DIFFERENT SUBNET
Host
 ↓
Routing table
 ↓
Default/specific gateway
 ↓
Router
 ↓
Remote network

Private source
     ↓
NAT/PAT
     ↓
Public-facing source
     ↓
Internet

Routing
IP → Where should packet go?

ARP
Next-hop IPv4 → Which local MAC?

NAT
Private/public address translation

Traceroute
Observe responding hops toward destination



## SOC relevance 
Routing and NAT knowledge helps SOC analysts determine how traffic moves between networks, identify internal versus external systems, understand firewall and network logs, interpret translated addresses, troubleshoot connectivity, and reconstruct suspicious network communications.


