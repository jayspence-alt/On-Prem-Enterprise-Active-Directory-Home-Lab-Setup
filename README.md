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

- Step 1. Prepare Your Environment:

    - Install a hypervisor (VMware Workstation, VirtualBox, or Hyper-V):

      **- I will be using VirtualBox.**

    - Download ISO files for Windows Server and Windows 10/11 clients:

      **- I already have ISO files for Windows Server 2022, Windows 10, Kali Linux and PFSense.**
      
- Step 2. Create the Domain Controller (DC):

    - Deploy a VM running Windows Server:
  
      <img width="654" height="495" alt="Screenshot_1" src="https://github.com/user-attachments/assets/816a6c68-3ec3-4385-bc08-317cb1478b4d" />
      <img width="1042" height="785" alt="Screenshot_2" src="https://github.com/user-attachments/assets/94e94e5c-6030-4518-aba8-1de16bee4072" />
      <img width="1902" height="1016" alt="Screenshot_3" src="https://github.com/user-attachments/assets/6681ead3-b47b-4bf4-9ff6-5f805c53e5c8" />

        **- I will be using Windows Server 2022 Edition**
      
    - Change the PC name:
      
      <img width="693" height="236" alt="Screenshot_40" src="https://github.com/user-attachments/assets/4c2c5d38-53f1-46a0-8a44-fa792f699352" />

      Why: This is so it is easy to identify the Domain controller as well as to avoid future issues. (Hint: If you change your pc name after AD DS is added, the computer will give you a security trust relationship           error) 

    - Install the Active Directory Domain Services (AD DS) role:
  
      <img width="1544" height="941" alt="Screenshot_4" src="https://github.com/user-attachments/assets/388bdd74-852a-4af2-a4a4-e6c7235fc585" />
      <img width="1047" height="783" alt="Screenshot_5" src="https://github.com/user-attachments/assets/6d9dcac7-ed80-4a54-847a-399767745cba" />
      <img width="1075" height="808" alt="Screenshot_7" src="https://github.com/user-attachments/assets/f72a1358-7122-434c-8138-75dc962050f9" />
      <img width="788" height="569" alt="Screenshot_14" src="https://github.com/user-attachments/assets/883cd1db-bb76-4c15-818a-1e9ead8e5dbe" />
  
      **- I will be installing AD DS, DNS and Remote Access.**

      <img width="787" height="563" alt="Screenshot_15" src="https://github.com/user-attachments/assets/0f44e904-a9ce-42d6-bcc1-bdc1144702f5" />

      **-Making sure Group Policy Management is checked.**
      
      <img width="1033" height="777" alt="Screenshot_17" src="https://github.com/user-attachments/assets/0b6f8bdc-77a2-4645-bb2b-89cbd713abf3" />

      **-Checking Routing in order to configure NAT(Network Access Translation) which ends up installing DirectAccess and VPN.**
      
      <img width="1055" height="788" alt="Screenshot_18" src="https://github.com/user-attachments/assets/7a54d8d0-eaa1-4051-97a6-fb179c61f692" />
      
      
    - Promote the server to a Domain Controller and create a new forest (e.g., lab.local):

      <img width="1037" height="781" alt="Screenshot_19" src="https://github.com/user-attachments/assets/ef711ae7-edf3-43fe-a472-e3c111557fe5" />
      <img width="1036" height="778" alt="Screenshot_20" src="https://github.com/user-attachments/assets/76b3a1e7-a345-4ad1-9d96-6a43b8c89f1b" />

      **-This ends up changing to SecureAccess.local**
      
      <img width="1031" height="772" alt="Screenshot_21" src="https://github.com/user-attachments/assets/ea64ff71-e3aa-4a46-8451-cf2c56a9425e" />
      <img width="1147" height="853" alt="Screenshot_22" src="https://github.com/user-attachments/assets/90ed6ce3-87ae-413b-bb87-82c708881c6d" />

  -Step 3. Configure Supporting Services
      - Set up DNS within AD DS.
       - Earlier in Step 2 I installed DNS along with AD DS and Remote Access.  On this server there are 2 NICs, 1 will be for my WAN and will receive internet access from my home router while the 2nd will be used as            the DNS server for my internal virtual network.  So here is the static IP scheme for my DC.
       
       <img width="404" height="457" alt="Screenshot_67" src="https://github.com/user-attachments/assets/576e85df-33c6-403c-9dfb-e65b053fa163" />
       
     - Next, I configured NAT so that any computer on the network will receive the same public IP address.

       <img width="1035" height="776" alt="Screenshot_33" src="https://github.com/user-attachments/assets/5812ea7e-1e99-4e14-b362-a5bcfc34cfc4" />
       <img width="1052" height="773" alt="Screenshot_34" src="https://github.com/user-attachments/assets/887d7a51-236c-47d7-81e9-f5158e59a468" />
       <img width="1044" height="780" alt="Screenshot_36" src="https://github.com/user-attachments/assets/bc92b52b-1ede-41fd-8018-2d5a03cd7088" />
       <img width="1044" height="771" alt="Screenshot_37" src="https://github.com/user-attachments/assets/bf7182b5-c70f-4f95-9633-37e957caea7b" />
      
    - Optionally configure DHCP for automatic IP assignment.
      
       - First I will add the DHCP server role.
 
       <img width="793" height="564" alt="Screenshot_38" src="https://github.com/user-attachments/assets/af0d7806-a53b-45b8-915a-f0b918e92cd6" />
       <img width="1032" height="777" alt="Screenshot_39" src="https://github.com/user-attachments/assets/d2556196-1d8c-49e6-8a58-04e24c17467a" />

       - Next I will configure the DHCP scope.  For this scope I want to limit computers in the network to the 172.16.0.100-200/24 scope for now.  As well as I only want computers to have the same IP address for 24              hours, so we will configure that in our DHCP lease duration configuration. 

        <img width="690" height="443" alt="Screenshot_42" src="https://github.com/user-attachments/assets/1cb375eb-0b00-4fc9-a9e1-3427c6dbd5df" />
        <img width="631" height="441" alt="Screenshot_43" src="https://github.com/user-attachments/assets/f367acbc-3b3d-4546-99bf-36279fad163d" />
        <img width="596" height="443" alt="Screenshot_44" src="https://github.com/user-attachments/assets/c925cbd2-3cbe-4d04-bb20-4bfdb287bbe6" />
        <img width="635" height="458" alt="Screenshot_45" src="https://github.com/user-attachments/assets/c9064ac6-d95d-48c6-9c90-e2cb5cc7ee4c" />

  - Step 4. Build Organizational Units (OUs)

      - Create OUs for Users, Computers, and Admins.

      - Define a logical structure to simulate an enterprise.
      
  - Step 5. Create Users & Groups

    - Add standard user accounts, IT admin accounts, and security groups.

    - Apply role-based access control via group memberships.

  - Step 6. Apply Group Policy Objects (GPOs)

    - Configure password policies, software restrictions, or login banners.

    - Link GPOs to OUs to enforce enterprise-style policies.

  - Step 7. Join Client Machines

    - Deploy Windows client VMs.

    - Join them to the lab.local domain.

    - Verify login with domain credentials.

  - Step 8. Test & Explore

    - Sign in as different users to test permissions.

    - Apply and troubleshoot GPOs.

    - Practice administrative tasks and simulate real enterprise scenarios.

        





      
