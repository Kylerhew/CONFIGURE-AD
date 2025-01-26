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

- Step 1 - Create resource group in azure.
- Step 2 - Create Virtual Network and Subnet.
- Step 3 - Create Domain Controller.
- Step 4 - Set Domain Controller's NIC Private IP address to be static
- step 5 - Disable Windows Firewall for testing connectivity.
- step 6 - Setting up a client in Azure. 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/gQp00Ia.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Azure portal and create a new Resource Group. Mine is named Active-Directory-Lab.
</p>
<br />

<p>
<img src="https://i.imgur.com/4nEKlgS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a Virtual network. Make sure it is attached to previously created Resource Group. My virtual network is named Active-Directory-vnet. You can name this to whatever you want. 
</p>
<br />

<p>
<img src="https://i.imgur.com/B31fJhz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we need to create the Domain Controller by spinning up a Virtual machine. Make sure to attach this machine to the previously created Resource Group and Virtual network and then name the Domain Controller. In this case it's dc-1. Also make sure the regions stay the same across the entire resource group. In this case it is East US. 
</p>
<br />

<p>
<img src="https://i.imgur.com/gxDMeaX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
As the image use Windows Server 2022 Datacenter and make sure to use atleast 2 VCPUs when creating the image size. 
</p>
<br />

<p>
<img src="https://i.imgur.com/xxC6yzE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set a password and username and make sure to check the box to use existing server license. Leave it on port 3389 for when we have to RDP ( Remote Desktop) into our Virtual Machines. 
</p>
<br />

<p>
<img src="https://i.imgur.com/iAvjNPn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure before you review and create this machine that it is under the Virtual network we created. Active-Directory-vnet. Them click on Review + Create and continue.  
</p>
<br />

<p>
<img src="https://i.imgur.com/bALnRC7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we have to create the client VM. It is the same as creating the dc-1 VM but we will name it client-1. Attach it to the resource Group aswell. 
</p>
<br />


<p>
<img src="https://i.imgur.com/Vuu74FI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the image size select Windows 10 pro also with atleast 2 VCPUs, create username and password, check the licensing box and Review + Create. 
</p>
<br />

<p>
<img src="https://i.imgur.com/3gaRV2a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Head back to dc-1 as we now have to set the NIC Private IP address to be stati. So under Virtual machines click on dc-1, go to the network settings and then click on the NIC ( Network Interface). The private IP adress is 10.0.04 in our case. 
</p>
<br />

<p>
<img src="https://i.imgur.com/79scoea.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on DNS server settings and under ipconfig change Private IP adrdress settings allocation from Dynamic to static. Then write in dc-1's private IP adress 10.0.0.4.
</p>
<br />

<p>
<img src="https://i.imgur.com/scv1DFt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now go to Virtual machines and find the public IP address for dc-1 our Domain Controller and we will use this to RDP into the VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/HRXoXQ1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Pull up Remote Desktop from the control panel ( start menu) and put in dc-1's public IP adress and username and password we created earlier during setup.
</p>
<br />

<p>
<img src="https://i.imgur.com/kBiJ1ln.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the VM is started up and we are in and everything we have done up until this point has been done correectly we should see the server manager pop up.
</p>
<br />

<p>
<img src="https://i.imgur.com/FISDJLb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First things firt, we need to disable the Firewall to test proper connectivety. Right click the start menu, click run and promt "wf.msc" which will bring up the firewall. Click on Windows Firewall properties and turn off Fire Wall state. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
































































