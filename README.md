# On-Prem-Enterprise-Active-Directory-Home-Lab-Setup
A home lab project simulating an on-premises enterprise Active Directory environment.  Includes domain services, OUs, GPOs, and domain-joined clients for practicing AD administration, identity management, and enterprise security in a safe, hands-on setup.

- The environment models a typical corporate IT infrastructure, including:

  - Windows Server Active Directory Domain Services (AD DS) for centralized authentication and user management.

  - Organizational Units (OUs), Group Policy Objects (GPOs), and role-based access control to replicate real enterprise policies.

  - Domain-joined Windows clients to test authentication, policy enforcement, and administrative tasks.

  - Optional integration with DNS, DHCP, and file/print services to mirror enterprise network dependencies.

- 🔹 Purpose:

  - Build and practice Active Directory deployment and administration skills.

  -  Explore common enterprise configurations in a safe lab environment.

  - Test security concepts such as user permissions, group policies, and account management.

  - Serve as a foundation for red team/blue team exercises or cybersecurity learning.

- 🔹 Use Cases:

  - Home lab setup for IT professionals and students.

  - Study environment for certifications (e.g., CompTIA Security+, Microsoft SC-900/SC-300, etc.).

  - Sandbox for testing GPOs, scripts, and administrative automation.

- 🚀 Setup Steps

**- Step 1. Prepare Your Environment:**

    - Install a hypervisor (VMware Workstation, VirtualBox, or Hyper-V).

      **- I will be using VirtualBox.**

    - Download ISO files for Windows Server and Windows 10/11 clients.

      **- I already have ISO files for Windows Server 2022, Windows 10, Kali Linux and PFSense.**
      
**- Step 2. Create the Domain Controller (DC)**

    - Deploy a VM running Windows Server.
      - <img width="654" height="495" alt="Screenshot_1" src="https://github.com/user-attachments/assets/1226627b-8847-4b34-9b8a-3be51499d2ea" />
      
        **- I will be using Windows Server 2022 Edition**
        
      - <img width="1042" height="785" alt="Screenshot_2" src="https://github.com/user-attachments/assets/13fa5a71-327b-400d-b106-cca9b15bf6fb" />
      - <img width="1902" height="1016" alt="Screenshot_3" src="https://github.com/user-attachments/assets/2319d20c-92a7-47c4-bc27-d429e5cd12e5" />

    - Install the Active Directory Domain Services (AD DS) role.
    
      - <img width="1544" height="941" alt="Screenshot_4" src="https://github.com/user-attachments/assets/867e2e5c-e3a0-40d4-9458-2569d9bcc0b8" />
      
      - <img width="1047" height="783" alt="Screenshot_5" src="https://github.com/user-attachments/assets/29780f02-507b-4ce4-a632-24a293f5ca5d" />
      
      - <img width="1075" height="808" alt="Screenshot_7" src="https://github.com/user-attachments/assets/a2c44e15-4cd1-4d4e-a464-f4de1b598d57" />
      
      - <img width="788" height="569" alt="Screenshot_14" src="https://github.com/user-attachments/assets/fb037c89-bac7-47af-b42b-2069617addf7" />
      
      - <img width="788" height="569" alt="Screenshot_14" src="https://github.com/user-attachments/assets/9ea2f52b-79ec-4249-9d60-a614c7433358" />



    - Promote the server to a Domain Controller and create a new forest (e.g., lab.local).
