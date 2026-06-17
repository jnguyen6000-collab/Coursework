Memo Report
**To:** Lisa Smith, IT Director   
**From:** John Nguyen  
**Date:**   
**Subject:** Zenmap Scan Analysis

1. What open ports are identified by the Zenmap scan?

	After the Zenmap scans 1000 ports on the laptop computer assigned to faculty, the Zenmap scan has identified 4 open ports. Those 4 open ports are port 135, port 445, port 139, and port 5357\. The service name for the following ports are listed under Port State Service Version. The service name for port 135 is Microsoft Window RPC. RPC stands for remote procedure call. Microsoft Windows RPC service provides communication so that clients can communicate with the server(Microsoft, 2019). This enables users to determine what services are available to them and what services are running (Cohen, 2024). The service name for port 139 Microsoft Windows netbios-ssn. Microsoft Windows netbios-ssn is a service that allows SMB over NetBIOS sessions when sharing files and printers over a network between 2 devices (Cohen, 2023). The service name for port 445 is Microsoft DS. Port 445 uses the Service Message Block (SMB) protocol which allows users to share resources such as files within the network using TCP (Cohen, 2023). The service name for port 5357 is Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP). According to an article by *Port 5357 – WSDAPI,* Port 5357 uses web services for devices which enables users to communicate with other network-connected devices.

2. What does the TCP Sequence Prediction entry refer to? What does the difficulty score mean?

TCP Sequence Prediction entry refers to predicting the sequence numbers used to identify the packets in TCP connection (Bellovin,1989). A TCP sequence is a 32-bit long number. If the attacker manages to successfully predict the sequence number of the host, the attacker can send a counterfeit packet into the TCP connection. The attacker can commit various cyber attacks such as denial of service. According to the Nmap scan provided the score is 254 which tells us it is very difficult to crack and reduces the chance of an attacker gaining unauthorized access. The difficult score in the TCP determines how hard or easy it is to guess the sequence number. 

3. Determine if the system is currently protected and which ports and services likely need to remain open. Describe at least two countermeasures or protection mechanisms that should be applied to this laptop and similar systems at the college.

	The system is currently not protected and at risk of data breach. In the beginning, it was already identified that 4 ports were open. If the system is not properly protected, it may provide the attacker with ways to infiltrate the network. All of these ports need to remain open in order to maintain Windows Active Directory functions. However, all of them are at risk of potential threats if not properly protected. In the scan, it reads "microsoft ds?” which could mean that they were unable to identify it. Furthermore, it also states that the message signing is enabled but not required which is a vulnerability in the system that could be exploited. SMB provides protection for data in transit by giving them encryption and signing which prevents unauthorized access  (Microsoft 2025). There are many different countermeasures or protection mechanisms that can be applied to his laptop and similar systems at the college. One of them is by adding a firewall and applying the deny by default rule. By applying the deny by default rule to a fire, all incoming network traffic will be blocked which will reduce an attacker from gaining unauthorized access (Parvez, 2026). The firewall setting can be changed to filter out the network traffic as well. However, firewalls also need to be maintained so updates are necessary to patch up vulnerabilities to prevent exploits. Another possible countermeasure to apply to laptops and other similar devices is to segment the network by using a guest network or VLAN (Parvez, 2026). If the attacker gains access to a device connected to a guest network, it will not be able to reach any other personal devices.

References  
Bellovin, S. M. (1989). *Security problems in the TCP/IP protocol suite*. ACM SIGCOMM Computer Communication Review, 19(2), 32–48. [https://doi.org/10.1145/378444.378449](https://doi.org/10.1145/378444.378449) 

Cohen, C. (2024, June 13). *What is port 135?* CBT Nuggets. [https://www.cbtnuggets.com/common-ports/what-is-port-135](https://www.cbtnuggets.com/common-ports/what-is-port-135) 

Cohen, C. (2023, October 20). *What is port 139?* CBT Nuggets. [https://www.cbtnuggets.com/common-ports/what-is-port-139](https://www.cbtnuggets.com/common-ports/what-is-port-139) 

Cohen, C. (2023, October 20). *What is port 445?* CBT Nuggets. [https://www.cbtnuggets.com/common-ports/what-is-port-445](https://www.cbtnuggets.com/common-ports/what-is-port-445) 

GeeksforGeeks. (n.d.). *Wrap around concept and TCP sequence number*. [https://www.geeksforgeeks.org/computer-networks/wrap-around-concept-and-tcp-sequence-number/](https://www.geeksforgeeks.org/computer-networks/wrap-around-concept-and-tcp-sequence-number/) 

Microsoft. (2019, August 23). *Microsoft RPC – Win32 apps*. Microsoft Learn. [https://learn.microsoft.com/en-us/windows/win32/com/microsoft-rpc](https://learn.microsoft.com/en-us/windows/win32/com/microsoft-rpc)

Microsoft. (2025, November 27). *What is SMB file sharing for Windows and Windows Server?* Microsoft Learn. [https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview](https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview) 

Parvez, H. (2026, January 15). *What is an open port? A guide to network vulnerabilities*. ExpressVPN. [https://www.expressvpn.com/blog/what-is-an-open-port/](https://www.expressvpn.com/blog/what-is-an-open-port/) 

*Port 5357 – WSDAPI (Web Services for Devices).* (n.d.). PentestPad.   
[https://itigic.com/tcp-sequence-prediction-attack-how-does-it-affect/](https://itigic.com/tcp-sequence-prediction-attack-how-does-it-affect/)

[Nguyen-FinalProjectPart1.md](https://github.com/user-attachments/files/28985784/Nguyen-FinalProjectPart1.md)



**To:** Lisa Smith, IT Director   
**From:** John Nguyen  
**Date:** March 30, 2026   
**Subject:** Netstat Command and Nessus Vulnerability Scan Analysis

1. Does the output indicate the presence of any Trojans? 

The output from the Netstat scan does not indicate the presence of a Trojan but it does reveal active connections along with the corresponding listening ports. Listening means that the port is open and actively waiting for a possible connection to be established. Established confirms that a connection has been made. There is a long list of lines that show TCP followed by the corresponding port number, laptop, and listening. The scan also shows that there are many connections that have been established to the local address 127.0.0.1 and 192.168.1.2. \[2603:8080:4500:19e6:a152:f0dc:63da:4954\] is an IPV6 address which was established. Towards the end of the scan, it shows the UDP section. Overall, there does not seem to be the presence of a Trojan.

2. What do you recommend to prevent Trojan infections in the future?

A trojan horse attack is a malware attack that disguises itself as a software that the user uses to trick them to install the malware (Sentinel 2025). If a Trojan horse attack is successful, the user may use precious data, financial information, data breaches, malware infections, etc. There are multiple ways to prevent a Trojan infection from happening in the future. My recommendation to prevent Trojan infections in the future is to implement network segmentation. If one segment gets compromised the damage only applies to that segment which further reduces the Trojan from infecting the entire network. Another way to prevent Trojans is to keep the system updated to patch up vulnerabilities that Trojan could exploit. Software updates also increase security and improve detection to possible threats.

3. For critical, high, medium, and low vulnerabilities detected by Nessus, describe each and how to resolve them.

 According to the Nessus vulnerability scan, the only vulnerability is a medium risk on the host ip address which is 192.168.1.2. The host was running on a Windows laptop. The vulnerability is that SMB signing was not required on the remote SMB server. This runs the risk of a remote attacker committing man in the middle attacks against the SMB server. The suggested solution on the Nessus scan is to enforce message scanning in the host configuration. On Windows, it can be found on the policy settings 'Microsoft network server: Digitally sign communications (always)’. Nessus also listed 26 info describing its findings on the laptop but they have no risk factors. Those items consist of services running like CPE, DCE, and RPC.

4. Research the top five malware-related threats that could affect servers, computers, and/or mobile devices at Rize. 

According to an AnyRun Malware Trend Report for 2025, the top five malware-related threats that could affect servers, computers, and mobile devices at Rize are Stealer, RAT, Loader, Ransomware, and Botnet. Stealer is a type of malware that is made to collect information from the user without them knowing ([Cyber.gov.au](http://Cyber.gov.au), 2025). RAT stands for Remote Access Trojan which involves tricking the user into installing the malware (Fortinet). Loader allows an attacker to interact with the compromised computer or bot (The Gurus, & The Gurus, 2018). Ransomware locks up the device until the user pays the money to the perpetrator. Botnet is an attack by controlling a group of devices connected to the internet infected by malware which allows the attacker to launch coordinated attacks (Palo Alto Networks, 2019).

1. Have any of the threats remained constant from year to year? Why?   
2. What threats do you believe will become more critical in the next 12 months? Why?  
3. What is the likelihood of an exploit affecting Rize, and which operating system(s) does it target?

The chart from the AnyRun Malware Trend Report shows that Stealer, RAT, Loader, Ransomware, and Botnet have remained constant from year to year. It emphasizes that the malware threats have grown to become more dangerous resulting in long-term impacts. These different types of malware threats continue to be used because it proves to work effectively against their victims. Furthermore, it seems the attackers want to steal sensitive info which can be used to commit many crimes or they sell this information to others. The threats I believe will become more critical in the next 12 months are likely Stealer and RAT because it enables cybercriminals to prepare for more large-scale attacks which gives them unauthorized access to the users credential information remotely. The likelihood of an exploit affecting Rize is high because there are many attack vectors that cybercriminals can use to send malware to the user such as phishing, suspicious downloads, or devices that lack security. The threats mainly target Windows operating systems which Rize uses for their devices. Even botnets can affect devices connected to the internet which put BYOD at risk.

4. Describe the five threats, including information to the questions above, and recommend ways to protect Rize’s systems and devices against those threats.

My recommendation to protect users from Stealer and Ransomware is to set up multi-factor authentication which prompts the user extra steps to verify their identity. I would also advise the user to enforce a strong password policy with special character, character count, and numbers. To protect users from RAT, Loaders, and Botnets, it is advised to train employees to be aware and keep your software updated to patch up any vulnerabilities in the system.

References  
ANY.RUN. (2026, January 20). *Malware Trends Report 2025: New Security Risks for Businesses in 2026*. ANY.RUN’s Cybersecurity Blog; ANY.RUN’s Cybersecurity Blog. [https://any.run/cybersecurity-blog/malware-trends-2025/](https://any.run/cybersecurity-blog/malware-trends-2025/)   
*Information stealer malware | Cyber.gov.au*. (2025). Cyber.gov.au. [https://www.cyber.gov.au/threats/types-threats/malware/information-stealer-malware](https://www.cyber.gov.au/threats/types-threats/malware/information-stealer-malware)   
Palo Alto Networks. (2019). *What is a Botnet?* Paloaltonetworks.com. [https://www.paloaltonetworks.com/cyberpedia/what-is-botnet](https://www.paloaltonetworks.com/cyberpedia/what-is-botnet)   
SentinelOne. (2024, September 26). *What Is a Trojan Horse? Types & Prevention*. SentinelOne. [https://www.sentinelone.com/cybersecurity-101/threat-intelligence/what-is-trojan-horse/](https://www.sentinelone.com/cybersecurity-101/threat-intelligence/what-is-trojan-horse/)   
The Gurus, & The Gurus. (2018, August). *Malware Loaders Continue to Evolve, Proliferate*. IT Security Guru. [https://www.itsecurityguru.org/2018/08/01/malware-loaders-continue-evolve-proliferate/](https://www.itsecurityguru.org/2018/08/01/malware-loaders-continue-evolve-proliferate/)   
*What Is a Remote Access Trojan (RAT)?* (n.d.). Fortinet. [https://www.fortinet.com/uk/resources/cyberglossary/remote-access-trojan](https://www.fortinet.com/uk/resources/cyberglossary/remote-access-trojan) 

[Nguyen-FinalProjectPart2.md](https://github.com/user-attachments/files/28985796/Nguyen-FinalProjectPart2.md)




**To:** Lisa Smith, IT Director   
**From:** John Nguyen  
**Date:** April 18, 2026   
**Subject:** Network Traffic Analysis and Rogue Access Point (AP) Detection Memo Report

(a) What was the first connection made, to where, and via what protocol?  
	The network packet captures shows that the first connection was made in the first line. The IP address 192.168.2.62 using the port 44389 connected to IP 192.168.2.104 using the port 22\. The S flag and the ack flag indicate that the protocol is TCP.

(b) What website did the user visit? What port was used in the connection?  
In the first line, it seems the user visits google. The user used port 36182 to connect with port 53 to visit google. The lines after that show that the user was trying to connect IP 192.168.2.62 on port 60175 with IP 74.125.95.103 on port 80\. The connection is not encrypted.

(c) What is different about this connection to the same site as in question 1(b)? Explain what was different and any significant outcomes.  
The connection shown here was trying to connect with [www.l.google.com](http://www.l.google.com) which is different from the domain that question b was trying to connect to. In this scenario, the connection uses the IP 192.168.2.62 on port 44190 to connect with 209.85.225.104 on port 443\. According to CBT Nuggets, port 80 uses HTTP while port 443 uses HTTPs. The significant and different outcome from part b is that it uses port 443 which makes the network traffic now encrypted. 

(d) What is occurring in the following traffic capture? What tells you this?  
It seems like the IP 192.168.2.104 with the port 52386 is trying to make a connection with numerous different ports on the IP 192.168.2.62. Those ports include 5900, 110, 22, 1025, 135, 199, 23, 993, 80, 587, and 139\. This tells us that the user is possibly searching for an open port.

e) Research and describe how to detect rogue APs. Translate your technical findings into the potential impacts for the school.

According to an article by Nile, a rogue APs is an unauthorized device or wireless access point connected to the network without the user’s permission. To detect rogue APs, the user can monitor their network, use wireless scanning tools, and install security software. Network monitoring checks unknown devices and watches for suspicious activities within the network. Wireless scanning tools find Wifi signals that do not match with the school's security configuration. Security software can detect threats in real-time. The dangers of having an existing rogue access point at a school could lead to data breaches which allows attackers to gain access to confidential information and damage the organization reputation. It could also potentially cause performance problems and the spread of malware to other devices.

(f) Finally, end with a section where you propose mitigation strategies for each identified vulnerability or anomaly.

	In the first vulnerability, it was identified that a connection was made between IP 192.168.2.62 using the port 44389 to IP 192.168.2.104 using port 22\. To migrate from this vulnerability, the school should enforce a stronger authentication such as multi-factor authentication which gives extra steps to verify the user’s identity. The second vulnerability is that the user visited Google. To migrate this vulnerability, the school should set up a firewall and filter the network traffic to block suspicious activity. The third vulnerability was when the user switched ports. To migrate this risk, the school should suggest training employees to be more aware of what encryption is. The fourth vulnerability contained multiple port scans. I would suggest applying a firewall to block all network traffic on unused ports. Lastly, for rogue APs, I would recommend the user to establish robust zero trust network security policies to define clear rules with all existing access points.

References  
CBT Nuggets. (n.d.). *HTTP Port 80 vs HTTPS Port 443: What’s the Difference?* [https://www.cbtnuggets.com/blog/technology/networking/http-80-vs-https-443](https://www.cbtnuggets.com/blog/technology/networking/http-80-vs-https-443)   
Cisco. (n.d.). *How to handle rogue access points in a Cisco Unified Wireless Network.* [https://www.cisco.com/c/en/us/support/docs/wireless/4400-series-wireless-lan-controllers/112045-handling-rogue-cuwn-00.html](https://www.cisco.com/c/en/us/support/docs/wireless/4400-series-wireless-lan-controllers/112045-handling-rogue-cuwn-00.html)   
Nile Secure. (n.d.). *What is a rogue access point & how to protect against them*. [https://nilesecure.com/network-security/what-is-a-rogue-access-point-how-to-protect-against-them](https://nilesecure.com/network-security/what-is-a-rogue-access-point-how-to-protect-against-them)   




