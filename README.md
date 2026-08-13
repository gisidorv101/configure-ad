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
Then on Client-1, we are going to set the DNS to DC-1's private IP, so go on DC-1, find the private IP address,s and then go back into clinet-1/ networking/ network settings/ network interface/ DNS servers. and then change it from "inherit from VM" to "custom" and put in the private IP address, then restart the VM on Azure
</p>
<br />
<h3>Step 4.</h3>
DC-1
<img width="1178" height="552" alt="Screenshot 2026-08-12 at 8 00 33 PM" src="https://github.com/user-attachments/assets/2634d1fa-301c-4415-8287-95559da985bf" />
Client-1
<img width="1613" height="954" alt="Screenshot 2026-08-12 at 8 04 37 PM" src="https://github.com/user-attachments/assets/9e268655-f3c8-4ea4-9c02-6c0740fbddb1" />


Log into DC-1 and ping the IP to see if it's running properly by going into PowerShell and typing "ping 10.x.x.x" Once that's all don,e go back into Client-1, open PowerShell, and type "ipconfig/all; the DNS output should be DC-1 private network
</p>
<br />
<h3>Step 5.</h3>

<img width="1664" height="964" alt="Screenshot 2026-08-12 at 8 49 19 PM" src="https://github.com/user-attachments/assets/353522f2-756e-4a6b-9eab-3f6a57dac15e" />

<img width="1665" height="962" alt="Screenshot 2026-08-12 at 8 49 41 PM" src="https://github.com/user-attachments/assets/a262bb6c-91be-4c12-86a9-9b1ace27f1ec" />

<img width="1660" height="948" alt="Screenshot 2026-08-12 at 8 48 31 PM" src="https://github.com/user-attachments/assets/c131d790-9dcf-4cbc-ba78-3b64c8f4810f" />
</p>
<br />
<h3>Step 6.</h3>

Back on DC-1, we are now going to make the Active Directory. Start off by launching Server Manager and clicking "Add roles and features"/ next/ next/ next/ Active Directory Domain Services/Add Features/Next/Next/Check the box "restart" and "yes" / Install. After that, we are gonna click on the little flag icon at the top right corner 
</p>
<br />
<h3>Step 7.</h3>
<img width="307" height="245" alt="Screenshot 2026-08-12 at 8 52 34 PM" src="https://github.com/user-attachments/assets/efe2f574-a3dd-44c1-a75b-5a6649d609ef" />

<img width="702" height="509" alt="Screenshot 2026-08-12 at 8 52 48 PM" src="https://github.com/user-attachments/assets/cebd16f3-c9d2-458e-8d4e-bde3c3c58419" />

<img width="407" height="209" alt="Screenshot 2026-08-12 at 8 58 27 PM" src="https://github.com/user-attachments/assets/8c85d2ea-2180-41ac-98c2-c069914d591e" />

Once we click the flag, we click on "promote this server to a domain controller" and then name our domain. Follow the prompts till completion and the account will reset. Log back into account using "domain\user"
