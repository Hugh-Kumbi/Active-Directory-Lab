# Active-Directory-Lab

## Description

This project details how I built an Active Directory home lab environment using VMware. I began by installing Microsoft Server and configuring it to host Active Directory services. Following that, I established a Domain Controller to manage the domain operations. Once the domain was set up, I ran a PowerShell script that generated over 1,000 user accounts in Active Directory. I then logged into several of these newly created accounts on a separate client machine, which was connected to the domain and had internet access. The lab served as a simulation of a corporate network environment. For this setup, I utilized a Microsoft Server 2019 ISO, a Windows 10 Enterprise ISO, VMware, and a PowerShell script.

## Tools and Technologies Utilized

**Active Directory**
- For managing domain services and creating user accounts in a simulated business environment.

**PowerShell**
- To automate the creation of over 1,000 user accounts in Active Directory.

**CMD**
- For additional system commands and configurations during the lab setup.

## Environments Deployed

**VMware**
- Virtualization platform for hosting the lab environment.

**Microsoft Server 2019**
- Operating system for running Active Directory and managing the domain.

**Windows 10 (21H2)**
- Client machine used for testing domain connectivity and user logins.

## Resources and Download Links

**VMware Workstation Player**

[VMware Workstation Player Evaluation](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion)

**Microsoft Server 2019 ISO**

[Download Windows Server 2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)

**Windows 10 ISO**

[Download Windows 10 ISO](https://www.microsoft.com/en-us/software-download/windows10)


![image](https://github.com/user-attachments/assets/3bd13a51-734c-49bd-8580-80e8bc9703fa)

## Program Walkthrough

The network schematic I'll be utilizing for this project:
![68747470733a2f2f692e696d6775722e636f6d2f496678766f59532e706e67](https://github.com/user-attachments/assets/ac7f9415-36a9-4c20-bdb8-984e6e1b410f)


Setting Up VMware and Virtual Machines

I used VMware Workstation Player to create two virtual machines:
DC (Server19): This virtual machine runs Microsoft Server 2019 and is configured as a Domain Controller (DC) to manage the domain.
Client1 (Win10): This virtual machine runs Windows 10 (21H2) and is used as a client to test domain connectivity.
Configuring the Domain Controller (DC)

The Domain Controller was assigned two NICs (Network Interface Cards):
NIC (Internet): Configured to obtain an IP address automatically using DHCP from the home router for external internet access.
NIC (Internal): Configured with a static IP address (172.16.0.1) to serve the internal network.
I installed the Active Directory Domain Services (AD DS) role and promoted the server to a Domain Controller with the fully qualified domain name (FQDN) mydomain.com.
Additionally, the DHCP role was configured with a single scope to assign IP addresses to internal clients. The DHCP range was set to 172.16.0.100–172.16.0.200, and DNS services were configured to point to the DC’s internal IP.
Running the PowerShell Script to Create Users

After setting up the domain, I executed a PowerShell script on the Domain Controller, which generated over 1,000 user accounts in Active Directory.
Each user account was automatically assigned a unique username and password as specified in the script.
Configuring the Windows 10 Client

On the Client1 (Win10) machine, I connected the internal NIC to the VMware network and joined the machine to the domain mydomain.com.
The client received its IP address and DNS configuration from the Domain Controller via DHCP.
I verified the setup by successfully logging in with several of the newly created domain user accounts and accessing the internet through the configured network.
Simulating a Business Environment

This lab environment simulated a typical corporate network setup where a Domain Controller manages user accounts, provides IP addresses, and ensures domain connectivity for client machines.


