Overview
This lab focused on creating GPOs, editing password policies, linking GPOs, and auditing changes.

Findings & Screenshots
EventLogGPO Settings

<img width="711" height="461" alt="Screenshot 2026-06-16 at 11 43 19 AM" src="https://github.com/user-attachments/assets/939a1ab7-9718-40f6-b05b-543db5e5378c" />


Explanation:  
Log sizes were increased to 4GB with retention set to “As needed.”

Linked EventLogGPO

<img width="711" height="461" alt="Screenshot 2026-06-16 at 11 43 42 AM" src="https://github.com/user-attachments/assets/28fabc17-9d66-4775-b129-7bc80cc060b5" />

Explanation:  
The GPO was linked at the domain root and applied to all authenticated users.

Default Domain Password Policy Changes

<img width="711" height="442" alt="Screenshot 2026-06-16 at 11 43 57 AM" src="https://github.com/user-attachments/assets/447a073c-cf0d-44a4-bb3e-653021ab01dd" />

Explanation:  
Password policy updated:

Minimum length: 8

Maximum age: 90 days

Complexity: Enabled

RSoP Report


<img width="711" height="442" alt="Screenshot 2026-06-16 at 11 44 18 AM" src="https://github.com/user-attachments/assets/65adb339-6bc2-4500-9a3b-b8fe3df6adf3" />


Explanation:  
RSoP confirmed the application of Default Domain Policy, EventLogGPO, and Domain Controller GPO.

What I Learned
How to configure and link GPOs

How password policies affect domain security

How to verify GPO application using RSoP
