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
