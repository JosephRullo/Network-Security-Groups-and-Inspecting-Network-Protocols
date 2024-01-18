<p align="center">
<img src="https://i.imgur.com/BTZI3Hv.jpg" height=100% width=100% alt="Traffic Examination"/>
</p>

<h1> <p align="center"> Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
<p align="center"> In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />
<p align="center"> <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
<br>
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, DHCP ,ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<h2>Step 2.</h2> 

**Create the Domain Controller Virtual Machine.** 
<p>
The computer where Active Directory will be installed is known as the Domain Controller. From the Azure homescreen select the "Virtual Machines" tab at the top. Click on "Create" -> select "Azure Virtual Machine". From this screen you will start in the "Basics" tab. In the Resource Group field below select "Create New" and assign it a name of your choice (for example ActiveDirectory). This "Resource Group" is where the Virtual Machine will be stored. Next assign a name of your choice in the "Virtual Machine Name" field (ex. DomainController-VM), this will be the name of your Domain Controller moving forward. For this example I will leave the other settings default, except for the "Image" field. Set "Image" to "Windows Sever 2022 Datacenter: Azure Edition". Next scroll down and in the "Size" field select the option with 2vcpus and 16 Gib of memory. In the Administrator account section just below, assign a username and password (store in a secure place in case you forget it). Now we can click "Review+Create" at the very bottom. Once "Validation" has passed you can click "Create" once more at the bottom of the window. This may take a few minutes to complete.
<p>
<p>
<img src="https://imgur.com/ddZi8Wm.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/5Tr1OM0.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/9kl2fML.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/T5b2S0X.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />
