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

  
        **- I will be using Windows Server 2022 Edition**

    - Install the Active Directory Domain Services (AD DS) role.
    


    - Promote the server to a Domain Controller and create a new forest (e.g., lab.local).
