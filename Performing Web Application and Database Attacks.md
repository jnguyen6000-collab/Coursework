Overview

This lab focused on testing vulnerable web applications using DVWA.
I practiced reflected XSS, stored XSS, SQL injection, UNION‑based SQL enumeration, and command execution attacks.
The goal was to understand how insecure input handling can lead to serious vulnerabilities.

Findings

DVWA

<img width="691" height="384" alt="Screenshot 2026-06-16 at 2 04 58 PM" src="https://github.com/user-attachments/assets/6ce4ad14-1e59-4cc6-b4f5-7c430a5a0845" /> 

Explanation:
Entering <John> showed how DVWA directly reflects user input into the HTML without sanitizing special characters.

Popup

<img width="691" height="384" alt="Screenshot 2026-06-16 at 2 06 33 PM" src="https://github.com/user-attachments/assets/85525723-f36c-4fc8-8305-51b5d8178edd" />

Explanation:
Injecting a <script>alert('vulnerable')</script> payload caused the browser to execute JavaScript, proving the page is vulnerable to reflected XSS.


<img width="691" height="384" alt="Screenshot 2026-06-16 at 2 09 36 PM" src="https://github.com/user-attachments/assets/0452ac16-71af-4289-b2a2-d4be1a08627e" />

Explanation:  
Submitting the following message stored malicious JavaScript on the server:


SQL Injection – Syntax Error 

<img width="691" height="145" alt="Screenshot 2026-06-16 at 2 12 43 PM" src="https://github.com/user-attachments/assets/9a0143a3-25f0-48d8-8208-8ae2633d5d68" />


Explanation:  
Entering O'Malley caused a SQL syntax error, confirming that user input is inserted directly into SQL queries without escaping.

SQL Injection – Boolean-Based Injection 

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 14 07 PM" src="https://github.com/user-attachments/assets/0a8162fa-3fb7-4df9-a93f-317523dc2b01" />


Explanation: 

The payload x'='x always evaluates to TRUE, causing the database to return all user records.

 ORDER BY Enumeration
ORDER BY 3 Error

 <img width="691" height="395" alt="Screenshot 2026-06-16 at 2 14 48 PM" src="https://github.com/user-attachments/assets/db0ff762-3ebd-440b-8e4d-09cf2b90c3b5" />

Explanation:  
Testing ORDER BY 1, ORDER BY 2, and ORDER BY 3 revealed the query only has two columns.

Invalid Column Name

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 16 01 PM" src="https://github.com/user-attachments/assets/512d4aba-9eb5-4065-8a84-dcc44e3a37c2" />


Explanation:  
Trying to reference a non‑existent column confirmed the structure of the underlying table.

 UNION Enumeration of Tables

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 16 15 PM" src="https://github.com/user-attachments/assets/4a861bce-9500-4cfc-8532-e2e024f01dc8" />


Explanation:  
Using UNION allowed listing database schemas and table names.

Extracting Usernames & Hashes

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 17 00 PM" src="https://github.com/user-attachments/assets/6005edcb-5b59-45e1-b984-cf172dac2007" />


Explanation:  

The UNION attack retrieved MySQL usernames and password hashes, showing full database compromise.

Command Injection

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 17 49 PM" src="https://github.com/user-attachments/assets/e7e189b4-350d-4cf6-993e-845fb6262bdf" />


Explanation:  
The command injection vulnerability allowed reading system files.

<img width="691" height="395" alt="Screenshot 2026-06-16 at 2 19 26 PM" src="https://github.com/user-attachments/assets/bef97837-1860-45bd-a2ca-844c52f68b58" />



Explanation:  
The server executed system commands, confirming remote command execution.

What I Learned

How reflected and stored XSS attacks work and how to identify them

How SQL injection can reveal database structure and extract sensitive data

How UNION‑based SQLi can enumerate tables and dump credentials

How command execution vulnerabilities allow system‑level access

The importance of sanitizing user input and restricting system commands

Tools Used
DVWA (Damn Vulnerable Web Application)

MySQL 

JBL Learning



Scenario: You are attempting to strengthen the security of your company’s e-commerce web application. You send a message to the staff developers requiring the next version to use proper design principles that will prevent buffer overflows.

1. Will a more secure design of your web application also minimize the effects of a denial of service (DoS) or distributed denial of service (DDoS) attack on your web server? Why or why not?  
   According to Microsoft 365, buffer overflows are the most common denial of service attacks because it causes the system to crash. A more secure design for my web application would reduce effects of a specific type of denial service attack directed towards buffer overflows but that would not stop the other types of DOS attacks. Microsoft defines a DOS attack as an attempt to overload a server or computer network with information. Attackers have many other ways to execute denial of service attacks. Some other ways for attackers to send DOS attacks is through IP data, the network’s bandwidth, DNS, etc.  
2. Reflect on the process of gaining authorization before conducting a penetration test. Why is this an essential step, and what could be the legal and ethical implications of failing to secure proper authorization?

According to Cyberly, penetration testing is also known as ethical hacking which is a practice in cybersecurity to identify possible existing vulnerabilities in the system that could be potentially exploited. The process of gaining authorization is important before conducting a penetration test because it ensures the penetration testers have legal rights to conduct the test with the organization they contracted with. A penetration test that attempts to access a system without authorization is considered illegal and unethical hacking which can result in crime charges, reputation damage, and legal action. If a penetration tester does not go through the process of authorization, they put themselves at risk of committing a crime under laws such as the Computer Misuse Act 1990 or the Computer Fraud and Abuse Act.

3. Discuss how the vulnerabilities you have explored in this lab might affect an organization's overall security posture. How do these vulnerabilities interact with other security controls and policies that an organization might have in place?

		According to Microsoft, security posture is the organization's ability to defend against cyberthreats by using their tools, planning, and training. There are many possible vulnerabilities that I have explored in this lab that might affect the organization’s overall security posture. In the lab, I have seen in the XSS attack that data can be manipulated and commands can break the page resulting in errors. This matters because the attacker can manipulate data on the website. In the lab, I learned how SQL injections enabled attackers to retrieve sensitive information like a list of ID’s, names and surnames. This matters because an attacker can steal credential information or any other sensitive information with SQL injections. The command injection showed me data on the device like the IP address and ping statistics. This matters because the attacker can use command injections to understand what devices their victims are using. SentialOne describes security misconfiguration when admin interfaces are exposed, default credentials are unchanged or poor permissions configurations which can be exploited by the attacker. These vulnerabilities matter because they can interact which can either weaken or bypass other security controls and policies that organizations might have in place. 

References  
Cyberly. “What Are the Legal and Ethical Considerations in Penetration Testing?” *Cyberly.org*, 26 Nov. 2024, www.cyberly.org/en/what-are-the-legal-and-ethical-considerations-in-penetration-testing/index.html?  
Microsoft 365\. “DoS vs. DDoS Attacks: What’s the Difference?” *Microsoft 365*, 17 Feb. 2023, www.microsoft.com/en-us/microsoft-365-life-hacks/privacy-and-safety/dos-vs-ddos-attacks-whats-the-difference? Accessed 9 Apr. 2026\.  
SentinelOne. “What Is Security Misconfiguration? Types & Prevention.” *SentinelOne*, 20 Nov. 2024, [www.sentinelone.com/cybersecurity-101/cybersecurity/security-misconfiguration/](http://www.sentinelone.com/cybersecurity-101/cybersecurity/security-misconfiguration/).   
“What Is Security Posture? | Microsoft Security.” *Microsoft.com*, 2025, [www.microsoft.com/en-us/security/business/security-101/what-is-security-posture](http://www.microsoft.com/en-us/security/business/security-101/what-is-security-posture). 



