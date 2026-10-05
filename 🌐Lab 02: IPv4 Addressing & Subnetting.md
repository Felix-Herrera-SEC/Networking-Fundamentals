# 🌐 Networking Fundamentals — Lab 02: IPv4 Addressing & Subnetting

## Objectives
Develop practical IPv4 addressing and subnetting skills by identifying network configurations, interpreting CIDR notation, calculating network and broadcast addresses, determining host ranges, and distinguishing private from public addressing.

## Skills Demonstrated
-IPv4 address interpretation

-Public vs. private IP 

-CIDR notation and subnet-mask interpretation

-Network and host address identification

-Network and broadcast address calculation

-Usable host-range calculation

-Same-subnet determination

-Linux network configuration analysis

-Basic network-context analysis for security investigations

## Tools used

Bash commands:

hostname -I

ip addr

ip route

ipcalc

ping

## Steps performed
-Identified the IPv4 address and CIDR prefix assigned to a Linux endpoint

-Distinguished private, public, and loopback addressing

-Converted CIDR notation into subnet-mask information

-Determined network and host portions of IPv4 addresses

-Calculated network addresses, broadcast addresses, and usable host ranges

-Determined whether hosts belonged to the same subnet

-Verified subnet calculations using ipcalc

-Examined the endpoint's local routing information

-Applied IPv4 addressing knowledge to a simulated SOC network alert

## evidence (screenshots)

1) Understood that an ipv4 address is composed 32 bits and its divided into 4 octects separated by a . and each contain 8 bits of information, each octect can contain a decimal value from 0-255 therefore we can understand why this IP address (192.168.1.25) is valid but (192.168.300.25) is not valid, due to the 300 exceededing the limit of information (8 bits) an octact can contain.



Understood that underneath the decimal notation IPv4 addr are binary.

for example using the ip a 192.168.1.25 we can determine that the binary value of each octect is the following:

192 = 11000000
168 = 10101000
1 = 00000001
25 = 00011001

and so the same ip addr can be represented as 11000000.10101000.00000001.00011001


2) Understanding private vs public IPs, to be able to idenitify if an IPv4 is public or private I need to know the format of the IP, if it is using whats known as a private block or RFC1918 which are the following:

Private block and address range

10.0.0.0/8  -- 10.0.0.0 - 10.255.255.255                 
 
172.16.0.0/12 -- 172.16.0.0 – 172.31.255.255

192.168.0.0/16 -- 192.168.0.0 – 192.168.255.255


quick memorization for this would be to think:

if the ip starts with:

10. Always private
172.16-31 Always private
192.168 Always private

3) Understanding subnets , a subnet mask is represented by the /number after the host ip, in an ipv4 this number cannot exceed 32 bits, this is called CIDR or Classless inter-domain routing. the subnet reads as the ip + host + /number that cant exceed 32.

Understanding this helps you calculate the amount of Ips possible inside a subnet, with the general rule of thumb that the lower the subnet mask number is, the more possible amount of Ips can be used inside the subnet.


Calculating total possible subnet Ips I you subracts 32 from the number in the mask and then do 2 elevelated to that result.

To calculate the broadcast IP you take the total possible number of subnet Ips and subtract by 2 due to 1 being reserved for the network ID and the other reserved for the broadast network

To calculate host count you take the total possible number of subnet Ips and subtract by 2 due to 1 being reserved for the network ID and the other reserved for the broadast network

4) Usind the hostname -I command to see the Ipv4 of this machine and then used ip addr command to view information on the main interface.

<img width="767" height="330" alt="image" src="https://github.com/user-attachments/assets/7cf1d43b-96e6-45c4-8654-103f5ef3ab84" />

Based on this I was able to identify:

Interface: enp0s3
IPv4: 10.0.2.15
CIDR (subnet mask): /24

I also was able to identify that its a private IP based on the fact it falls inside the private block reference of 10.0.0.0/8 RFC1918

Calculting total amount of Ips and their types inside the subnet using subnet mask of /24

First I identified the following information:

Subnet Mask: /24

Network Address: 10.0.2.0

First Usable Host: 10.0.2.1

Last Usable Host: 10.0.2.254

Broadcast Address: 10.0.2.255

Total Addresses: 256

Usable Hosts: 254

5) installed and ran ipcalc on the IPv4 of the main interface to verify that my calculations where correct.

<img width="556" height="191" alt="image" src="https://github.com/user-attachments/assets/7f14b07a-5b7d-4cc9-846c-7fbeb1f80346" />

6) For the final subnet challenge I tried to find the following information for theis subnet 172.16.10.130/26

Private/Public: Private, falls into private block framework RFC1918

Subnet Mask: /26

Network: 172.16.10.128, calculated number and size of blocks, then broke down the block multiple to see in which block the host on the subnet falls into and used the start of the block containing the block number to identify the network.

First Host: 172.16.10.129, number of the network +1

Last Host: 172.16.10.190, number of the broadcast network -1

Broadcast: 172.16.10.191, the last number before the next block starts

Usable Hosts: 62, subtracted 32 bits for the CIDR number 26 (6), then did 2 to the power of 6 to get the number of usable hosts


## lessons learned

How to identify if a an IP is private or public using the RFC1918 framework, and understood the differece between a private network and a public one, also how the IPv4 are structured in 4 octects each containing 8 bits, and how to understand the subnet mask (CDIR) and that it represents the number of networking bits, also how to get the network ID, First and last Usable host Ips, the total number of usable hosts and the broadcast IP for the subnet.



## SOC relevance

IPv4 addressing and subnetting skills allow SOC analysts to distinguish internal and external systems, determine whether hosts belong to the same network, interpret CIDR ranges in security tools, and establish network context when investigating suspicious connections.

IPv4 addressing and subnetting skills allow SOC analysts to distinguish internal and external systems, determine whether hosts belong to the same network, interpret CIDR ranges in security tools, and establish network context when investigating suspicious connections.
