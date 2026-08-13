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
<img width="803" height="452" alt="Screenshot 2026-08-12 at 4 47 31 PM" src="https://github.com/user-attachments/assets/1357e025-6c9d-4a74-9367-d9996b991558" />
</p>
<p>
<p>
We are now gonna go into DC-1 setting and change to NIC from "Dynamic to "Static" by clicking on it and going to networking/ network settings/ network interface/ ipconfig1/ static. Then click ok
</p>
</p>
<br />

<h3>Step 3.</h3>
<p>
<img width="1430" height="792" alt="Screenshot 2026-08-12 at 7 56 31 PM" src="https://github.com/user-attachments/assets/0279197f-c2ac-4506-bc5c-9a81e3061906" />
</p>
<p>
<p>
Then on Client-1 we are going to set the DNS to DC-1 private IP, so go on DC-1 find the private IP adress and then go back into clinet-1/ networking/ network settings/ network interface/ DNS servers. and then change it from "inherit from vm" to "custom" and put in the private ip adress, then restart the vm on Azure
</p>
<br />
<h3>Step 4.</h3>
DC-1
<img width="1178" height="552" alt="Screenshot 2026-08-12 at 8 00 33 PM" src="https://github.com/user-attachments/assets/2634d1fa-301c-4415-8287-95559da985bf" />
Client-1
<img width="1613" height="954" alt="Screenshot 2026-08-12 at 8 04 37 PM" src="https://github.com/user-attachments/assets/9e268655-f3c8-4ea4-9c02-6c0740fbddb1" />


Log into DC-1 and ping the ip to see if its running properly by going into Powershell and typing "ping 10.x.x.x" Once thats all done go back into Client-1, open Powershell and type "ipconfig/all", the DNS output should be DC-1 private network
</p>
<br />
<h3>Step 5.</h3>

Back onto client-1 we are now going to make the Active Directory, start off by launching Server Manager and the clicking Add roles and features/ next/ next/ next/ Active Directory Domain Services/ Add Features/ Next/ Next / Check the box "restart" and "yes" / 
