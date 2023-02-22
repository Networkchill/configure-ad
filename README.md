# configure-AD
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
  
- Setup Resources in Azure 
- Create the Domain Controller VM (Windows Server 2022) 
- Take note of the Resource Group and Virtual Network (Vnet) that get created at this time
- Set Domain Controller’s NIC Private IP address to be static
- Create the Client VM (Windows 10). Use the same Resource Group and Vnet that was created prevoiusly.
- Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher)

</p>

<div>

  <img src="https://i.imgur.com/hLmM3bO.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/JgYYDpF.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/Uyc08Cc.png" style="width: 13.33%; float: left;">
  
</div>


<br />


<p>
  
- Ensure Connectivity between the client and Domain Controller
- Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)
- Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
- Check back at Client-1 to see the ping succeed
Install Active Directory
-Login to DC-1 and install Active Directory Domain Services
-Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
-Restart and then log back into DC-1 as user
  
  <img src="https://i.imgur.com/a3yzkXU.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/oNw03LQ.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/S9z3WoO.png" style="width: 13.33%; float: left;">

 
</p>
<br />
  


<p>
  
- Join Client-1 to your domain (mydomain.com)
  
- From the Azure Portal, set client DNS settings to the DC’s Private IP address
- From the Azure Portal, restart Client
- Login to Client (Remote Desktop) as the original local admin and join it to the domain (computer will restart)
-Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain
  
  </p>
  
  <p>

  <img src="https://i.imgur.com/JFXJ2jB.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/esjqOgK.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/mT0rbnd.png" style="width: 13.33%; float: left;">
    
  
    
</p>

<p>

Create a bunch of additional users and attempt to log into client-1 with one of the users
- Login to DC-1 
- Open PowerShell_ise as an administrator
- Run script and observe the accounts being created
  
  
  <img src="https://i.imgur.com/xpg5DXj.png" style="width: 13.33%; float: left;">
  
  <img src="https://i.imgur.com/Taqw6uy.png" style="width: 13.33%; float: left;">
  
    


<br />
