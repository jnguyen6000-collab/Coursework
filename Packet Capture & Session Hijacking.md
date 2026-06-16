Overview

This lab focused on learning how network traffic can be captured, inspected, and manipulated on a local network.
I practiced passive sniffing with Wireshark, active sniffing using ARP poisoning with Ettercap, and session hijacking using Burp Suite.
I also saw how insecure HTTP traffic can be intercepted and modified, and how HTTPS can still be attacked if the victim accepts an untrusted certificate.

Findings

Two ICMP packets in the Wireshark packet list

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 30 38 PM" src="https://github.com/user-attachments/assets/c0dece77-32b7-4e17-8807-e4023c85eb79" />

Explanation:  
Wireshark captured the ping request from 172.30.0.3 to 172.30.0.2 and the reply back. This confirmed that the interface was successfully capturing LAN traffic.

First Four Lines of HTTP Data

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 32 15 PM" src="https://github.com/user-attachments/assets/21d653df-ede7-406c-8748-c1b5bc006193" />

Explanation:  
After loading the To‑Do web page on vWorkstation, Wireshark captured the HTTP GET request and the server’s 200 OK response. The first lines showed the HTTP headers, proving that HTTP traffic was visible once ARP poisoning was active.


“A New Item” Added to the To‑Do List


<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 32 35 PM" src="https://github.com/user-attachments/assets/d1cb6fad-5575-441c-bd8a-941cd14e9554" />

Explanation:  
After ARP poisoning, I could see the victim’s HTTP traffic and confirm that the new to‑do item appeared on the page.


Burp Suite – Response to Adding Sneaky Item

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 32 52 PM" src="https://github.com/user-attachments/assets/0a032861-b54e-41db-a7dc-28dc56db1d37" />

Explanation:  
Burp Suite intercepted the POST request for adding a new item. The server responded with a 302 redirect, showing the request was accepted.


“A Sneaky Item” in the To‑Do List

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 33 06 PM" src="https://github.com/user-attachments/assets/e73f5e52-f3bb-4461-b680-6216ae23f3f2" />


Explanation:  
The manipulated request successfully added a new item to the victim’s list, proving session hijacking worked.


Applied Learning

ICMP and HTTP packets in Wireshark.

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 33 54 PM" src="https://github.com/user-attachments/assets/c0248bdd-b5ad-4810-8ac9-34eb5b998382" />

Explanation:  
Using arpspoof instead of Ettercap still allowed me to capture both ICMP and HTTP packets, confirming that ARP poisoning was successful.

 Certificate Details

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 34 24 PM" src="https://github.com/user-attachments/assets/d50d8af6-2636-467d-9898-dc043fa9b51b" />

Explanation:  
When intercepting HTTPS, the browser warned about an untrusted certificate. Viewing the certificate showed it was issued by “PortSwigger CA,” which is Burp Suite’s fake CA.


HTTPS Requests in Burp Suite

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 34 40 PM" src="https://github.com/user-attachments/assets/2298c268-8246-455c-99df-7743c9ef11ca" />

Explanation:  
Once the certificate was accepted, Burp Suite could read HTTPS traffic. The history showed GET, POST, and PUT requests from the victim.


 Request & Response details

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 35 20 PM" src="https://github.com/user-attachments/assets/5ef107a9-a706-4b1a-808e-0afc9fbfa516" />

Explanation:  
Burp Suite captured the PUT request used to update a to‑do item. The server returned a 200 OK, confirming the action succeeded.


HTTPS Hijack Response

<img width="691" height="417" alt="Screenshot 2026-06-16 at 2 37 35 PM" src="https://github.com/user-attachments/assets/f24962d2-3e5b-4c8b-b677-17939ccaa342" />

Explanation:  
Burp Suite showed the server’s response after modifying the victim’s HTTPS request, proving that HTTPS can be hijacked if the victim trusts the attacker’s certificate.


What I Learned

How to capture LAN traffic using Wireshark

How ARP poisoning works and why it enables MITM attacks

How Burp Suite can intercept and modify HTTP and HTTPS traffic

Why accepting untrusted certificates is dangerous

How session hijacking works on insecure networks

Tools Used

Wireshark

arpspoof

Burp Suite

JBL Learning

[Lab - Performing Packet Capture and Session Hijacking.md](https://github.com/user-attachments/files/29014712/Lab.-.Performing.Packet.Capture.and.Session.Hijacking.md)


* Scenario: As you learned in this lab, network sniffing is the act of observing communications on the network in either a passive or an active mode. With sniffing, you can see what is being transmitted unprotected on the network and potentially intercept sensitive information. Attackers use sniffers to compromise the confidentiality of data as it flows across a network.


1. In a university environment, what ethical concerns might exist for administrators when sniffing traffic?

An ethical concern that may exist for an administrator when sniffing traffic is invading users’ privacy, spying on the user, and stealing sensitive information which leads to trust issues within an university environment for the students and staff. Sensitive information that is at risk of being stolen may include passwords, financial information, emails, browsing history, etc. Hackers can use traffic sniffing to send malware into the packet to compromise anyone’s device connected to the network. Even though it does raise a lot of ethical concerns, there are some good ethical reasons to be sniffing traffic. Some of those reasons may include detecting networks and preventing attacks, ensuring network performance running smooth, ensuring strong network policies, etc. These reasons help ensure that traffic sniffing is used ethically and protect the students and staff in the university to some extent. Traffic sniffing is like a double edged sword. It can be used for good and evil intentions but it mainly depends on the user, in this case the administrators. 

2. Should you encrypt all network traffic to protect against unauthorized network sniffing? Why or why not?

Yes. I believe all network traffic should be encrypted to protect against unauthorized network sniffing. Encryption converts our data into unreadable format so that only a user with an encryption key can unlock it. By encrypting our data, we can reduce sensitive information from being intercepted. The encrypted data is less likely to be read or modified from a possible unauthorized network sniffing. This will prevent sensitive information from being stolen and devices from being compromised. There are many other ways to protect ourselves from unauthorized network sniffing but encryption is just one of them that is necessary for network protection.

References 

“Encrypted Network Traffic.” *LiveAction*, www.liveaction.com/glossary/encrypted-network-traffic/.  
“Network Sniffing & Packet Deconstruction: What You Need to Know | Tech Impact.” *Tech Impact*, 16 Aug. 2023, techimpact.org/news/network-sniffing-packet-deconstruction-what-you-need-know.  
