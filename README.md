<p align="center">
<img src="https://i.imgur.com/BTZI3Hv.jpg" height=100% width=100% alt="Traffic Examination"/>
</p>

<h1> <p align="center"> Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
<p align="center"> In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />
<p align="center"> <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
<br>
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remmina Remote Desktop
- PowerShell
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, DHCP ,ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resources in Azure
- Install Wireshark
- Add Network Security Group Rules
- Prompt Traffic Between VM's
- Observe Network Protocols 
  

<h2>Actions and Observations</h2>

<h2>Step 1.</h2> 

**Create Virtual Machines in Microsoft Azure.** 
<p>
For this tutorial we will be utilizing two Virtual Machines created in Azure running different Operating Systems. Begin by creating each VM setting up one running Windows 10, and the other running Linux (Ubuntu). Make sure to configure them so that they are sharing the same Virtual Network. For a more detailed walkthrough on creating Virtual Machines please view this link: <p>
https://github.com/JosephRullo/Azure-Virtual-Machines-and-Networking/blob/main/README.md
<p>
<p>
<img src="https://i.imgur.com/6xnHPwK.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/aSbJuL6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
<h2>Step 2.</h2> 

**Login to Windows VM using Remote Desktop.** 
<p>
First we will login to our Windows VM. Since I'm using a Linux based Host PC, I will login to the Windows VM using Remmina Remote Desktop (If your Host is running  Windows or Mac, simply use Microsoft's Remote Desktop).
<p>
<p>
<img src="https://i.imgur.com/qaQ2hnA.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/pkxhSVE.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
