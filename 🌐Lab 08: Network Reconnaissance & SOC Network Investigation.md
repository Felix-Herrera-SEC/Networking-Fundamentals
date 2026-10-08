# 🌐 Networking Fundamentals — Lab 08: Network Reconnaissance & SOC Network Investigation

## Objective
Perform authorized network reconnaissance and endpoint network analysis using Linux command-line tools. Identify active hosts, exposed TCP services, network connections, and potential security concerns while documenting findings using a structured SOC investigation methodology.

## Skills Demonstrated
-Network host discovery

-TCP port scanning

-Service identification

-Nmap scan interpretation

-Linux socket and process analysis

-DNS resolution and IP identification

-Local network enumeration

-Basic network exposure assessment

-Suspicious connection investigation

-SOC alert triage

-Security evidence collection

-Technical investigation reporting

## Tools used
nmap

ss

ip

dig

n

curl

python3

ping

traceroute

## Steps performed
1)Established a network baseline.

2)Performed authorized host discovery.

3)Identified exposed TCP ports.

4)Examined services and associated processes.

5)Generated controlled network activity.

6)Correlated scan findings with endpoint network data.

7)Investigated a simulated suspicious connection.

8)Documented findings and remediation recommendations.

## evidence (screenshots)

1)Established  a network baseline by running the ip -br addr command and the ip route command to view the routing table.

<img width="762" height="126" alt="image" src="https://github.com/user-attachments/assets/b7285aca-b190-4ba9-a790-56f159557e8d" />

Identified the following information.

Hostname: Ubuntu
Interface: enp0s3
IPv4: 10.0.2.15/24
Gateway: 10.0.2.2

2)Performed autorized host discovery using nmap command nmap -sn 127.0.0.1

<img width="531" height="92" alt="image" src="https://github.com/user-attachments/assets/2c7ba4c8-7f50-42a2-bb70-f5ad25c5792e" />

Based on this I was able to determine that the host is up.

3)Scanning TCP ports, scanned ports 22,80,443 and 8000 using the nmap -sT -p 22,80,443,8000 127.0.0.1

<img width="532" height="226" alt="image" src="https://github.com/user-attachments/assets/279688a4-0374-4f99-a690-bcc6e5be258e" />

I was able to determine that he ssh service was open but the others where closed.

3)Generated controlled network activity with this script: 

mkdir -p ~/soc-lab08-web

cd ~/soc-lab08-web

echo "SOC Lab 08" > index.html

python3 -m http.server 8000 --bind 127.0.0.1

<img width="660" height="455" alt="image" src="https://github.com/user-attachments/assets/2547c9cc-3306-48bb-b925-b919cdf3437d" />

and was able to verify the port state and service:

PORT       STATE   SERVICE
8000/tcp   open    http-alt

<img width="532" height="192" alt="image" src="https://github.com/user-attachments/assets/1977f7b3-68e7-4fd2-843d-563400dc2cd7" />


4)Examined services and assciated processes to determine which application is behind and open port using the command nmap -sV -p 8000 127.0.0.1

<img width="762" height="181" alt="image" src="https://github.com/user-attachments/assets/7060d4ab-4cc3-40ac-a8af-1a469de10019" />

and then used the curl -I http://127.0.0.1:8000 to verify that it responses to http request.

<img width="387" height="137" alt="image" src="https://github.com/user-attachments/assets/400757a8-97c4-49f6-bf96-3a7f1454a3fb" />

5)Matching open ports to proccesses, used the ss -tlpn | grep :8000 to isolate the socket and see that the process was owned by "python 3", then ran the ps aux | grep '[h]ttp.server' to see the command used to start the service. then generated traffic using the curl http://127.0.0.1:8000 and then used ss -tan to see the short lived connections.

<img width="806" height="392" alt="image" src="https://github.com/user-attachments/assets/f8e20072-df8f-4406-8e57-6462fbb3cac8" />

6)Correlated scan findings with endpoint network data used command nc -l 127.0.0.1 4444 to start local lister at port 4444, then ran nmap -sT -p 4444 127.0.0.1 and then sudo ss -ltnp and I could obeserve port 4444 listeinig with a netcat process associated with it.


<img width="762" height="582" alt="image" src="https://github.com/user-attachments/assets/224e0c77-c4bb-4847-bdb7-0f89b7e742f4" />


## SOC relevance 
Network reconnaissance and service enumeration help SOC analysts establish an endpoint's expected network behavior, identify unnecessary exposed services, investigate suspicious connections, and correlate firewall, SIEM, and endpoint telemetry.
