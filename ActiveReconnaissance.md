Overview


This lab focused on network discovery, host enumeration, OS fingerprinting, packet analysis, and vulnerability scanning using Zenmap, Wireshark, Nessus, and OpenVAS.

Findings & Screenshots
Ping Scan – Discovered Hosts

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 23 17 AM" src="https://github.com/user-attachments/assets/c40ae2bc-c662-4e04-9da5-d6e62ab9ced4" />

Explanation:  
A ping sweep identified active hosts across 172.30.0.0/24 and 172.31.0.0/24.

Host Details for 172.30.0.20

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 25 53 AM" src="https://github.com/user-attachments/assets/f6702a31-f1a2-4e70-8400-d6f793ed5dcc" />

Explanation:  
OS fingerprinting identified the host as Windows 7/Server 2008 family 

Here is the IP addresses and operating systems identified.
According to the host details, 172.30.0.20, 172.30.0.30, 172.30.0.40 run on the Mircosoft Windows
operating systems. To be exact, 172.30.0.20 runs Mircosoft Windows 7 SP0 - SP1, Windows Server
2008 SP1, Windows Server 2008 R2, Windows 8, or Windows 8.1 Update 1. 172.30.0.30 runs
Mircosoft Windows Server 2012 R2 Update 1. 172.30.0.40 runs Mircosoft Windows Server 2016.
172.31.0.40, 172.31.0.50, and 172.31.0.60 run Linux. 172.31.0.40 runs Linux 2.6.32. 172.31.0.50 runs
Linux 3.11 - 4.1. 172.31.0.60 runs Linux 2.6.15 - 2.6.26. For the remaining IP addresses, it seems like
no ports were open for 172.30.0.1, 172.30.0.2, 172.30.0.5, 172.31.0.1, and 172.31.0.4. There was no
operating system that could be identify for 172.30.0.1, 172.30.0.2, 172.30.0.5, 172.31.0.1, and
172.31.0.4.

Network Topology Map

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 28 39 AM" src="https://github.com/user-attachments/assets/bc6314a5-f717-4d4a-8922-a66bfda4575d" />

Explanation:  
Zenmap’s topology visualization revealed network structure and potential pivot points.

SYN Scan Packet Sequence

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 30 16 AM" src="https://github.com/user-attachments/assets/8e922d99-e824-4a81-b057-e92a366fe719" />

Explanation:  
Wireshark captured the SYN → SYN/ACK → RST handshake, confirming port 22 was open.

Nessus MS17‑010 Vulnerability

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 30 40 AM" src="https://github.com/user-attachments/assets/0cf2541a-422c-4320-bdb2-6e44e1455f25" />

Explanation:  
Nessus detected EternalBlue (MS17‑010), confirming the host was exploitable.


Vulnerability title and the Plugin information for MS17-010

<img width="678" height="427" alt="Screenshot 2026-06-16 at 8 33 19 AM" src="https://github.com/user-attachments/assets/12757c10-9770-4b7f-acca-ee7ab16e920b" />

Explanation:
Nessus describes the Vulnerability with Microsoft Windows update and suggest to patch the vulnerabilities up.

What I Learned
How to enumerate networks using Nmap/Zenmap

How to analyze packet flows in Wireshark

How to identify OS versions and open ports

How to detect high‑severity vulnerabilities using Nessus/OpenVAS

Tools Used

Zenmap

Wireshark

Nessus Essentials

OpenVAS
