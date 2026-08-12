<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create and prepare Azure virtual machines for the domain controller and client computer
- Install Active Directory Domain Services, promote DC-1, and create the mydomain.com domain
- Create organizational units and employee user accounts in Active Directory
- Join Client-1 to the domain and verify domain-user authentication
<h2>Deployment and Configuration Steps</h2>

<h3>Step 1.</h3>
<p>
<img <img width="2048" height="1156" alt="image" src="https://github.com/user-attachments/assets/16347994-edde-4982-9d3e-0d6e9c899d46" />
</p>
<p>
To start off, we are going to need two Azure virtual machines: DC-1 as the domain controller and client-1 as the client computer. Both virtual machines are sharing the same resource group and network
</p>
<br />

<h3>Step 2.</h3>
<p>
<img <img width="1693" height="929" alt="image" src="https://github.com/user-attachments/assets/b228e8dc-60b4-4d95-8f2a-a21b4398b7e5" />

</p>
<p>
<p>
I installed and configured Active Directory Domain Services on DC-1 and created the mydomain.com domain. I organized Active Directory using OUs for administrators, clients, employees, and groups, then created employee user accounts in the _EMPLOYEES OU.
</p>
</p>
<br />

<h3>Step 3.</h3>
<p>
<img <img width="2048" height="1214" alt="image" src="https://github.com/user-attachments/assets/f44df673-3831-40ee-a39e-4f11c51ef061" />
</p>
<p>
<p>
I joined client-1 to the mydomain.com domain and verified domain authentication by signing in as mydomain\jane_admin. The hostname command confirmed that the logged-in domain user session was running on client-1.
</p>
<br />
