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
For this tutorial we will be utilizing two Virtual Machines created in Azure running different Operating Systems. Begin by creating each VM setting up one running Windows 10, and the other running Linux (Ubuntu). Make sure to configure them so that they are sharing the same Virtual Network. Once the VM's are ready, take note of the Public and Private IP Addresses for each one located on the VM Overview page. For a more detailed walkthrough on creating and configuring Virtual Machines please view this link:
<p>
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
<h2>Step 3.</h2> 

**Download and Install Wireshark** 
<p>
Once signed in, open the web browser and go to https://www.wireshark.org/download.html and download Wireshark. Once downloaded, begin to install it with all the default settings.
<p>
<p>
<img src="https://i.imgur.com/hVHY2OV.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/qhav4o4.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

<h2>Step 4.</h2> 

**Open Wireshark and Observe Network Traffic** 
<p>
Once installed, go to the start menu and open the Wireshark app. Click the shark icon at the top left of the screen to begin "Capturing Packets" of traffic. You will notice lots of traffic activity now visible. This traffic is accross all Network Protocols that are going on in the backround of the Virtual Machine and it's remote connection to the Host.
<p>
<p>
<img src="https://i.imgur.com/yTtlOYb.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/YtOCctG.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/Z9lPXS6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
<h2>Step 5.</h2> 

**Filter ICMP Traffic and Ping Test** 
<p>
Let's now try a connection test between both VM's and filter Wireshark to see only that traffic. At the top of the Wireshark window, type the following "icmp" and hit enter. This is the protocol of the "ping" (connection test) we will send to the private IP Address of our secon VM running Linux. Now only ICMP protocol traffic will be displayed. Next go to the start menu (still inside Windows VM) and open PowerShell -> type the following command "ping 10.0.0.5" (this is the Private IP Address for VM-2) -> hit enter. This will send traffic to VM-2 and reply back to VM-1. Once this is entered in, you will see in PowerShell the connection test being established. Going back to Wireshark, you will see this traffic to and from each VM in more detail. Try another "ping" test this time to google. Type in PowerShell "ping www.google.com -4" and hit enter. This time you can see the ICMP traffic between VM-1 and Google.
<p>
<p>
<img src="https://i.imgur.com/vM3qUJ6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/XBd2wFc.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/scL5fpL.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/tTL9EpO.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/gh41KAA.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
<h2>Step 6.</h2> 

**Perpetual Ping** 
<p>
To set up the next step we will initiate a "Perpetual Ping" between VM-1 and VM-2. Let's clear the traffic in Wireshark by clicking on the green shark button at the top -> click "Continue Without Saving". Now go back to PowerShell and type in the following command "ping 10.0.0.5 -t" and hit enter. VM-1 will now continue sending a ping to VM-2 non-stop until you quit it.
<p>
<p>
<img src="https://i.imgur.com/YyFLfc7.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/s6Fz8DE.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/YpRRazC.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
<h2>Step 7.</h2> 

**Network Security Groups Inbound Rules** 
<p>
You can use an Azure network security group to filter network traffic between Azure resources in an Azure virtual network. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources. For each rule, you can specify source and destination, port, and protocol. Let's add a new "Inbound Security Rule" to block the "Ping" we are sending to VM-2. Mininmize the Remote Desktop to go back to your Host PC. From the Host go to Azure and search for "Network Security Groups" -> click to select it -> select VM-2 -> under "Settings" select "Inbound Security Rules" -> click "Add" at the top.
<p>
<p>
<img src="https://i.imgur.com/cisSjPS.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/L7PHAX6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/7AkQtNF.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/Gdhr6hU.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />
<h2>Step 7.</h2> 

**Network Security Groups Inbound Rules (continued)** 
<p>
You can configure the Inbound Security Rule in various ways, but for this test we will leave the top fields on the default settings. Scroll down to the "Protocol" selection and choose "ICMP" (you will not have to select a port since ICMP does not use one). Under Action select "Deny", this will block the Ping since it utilizes the ICMP Protocol. Set the "Priority" to a number less than the other security rules (this will ensure it has a higher priority). Finally assign it a "Name" describing it's function, then click "Add". Now go back to the Remote Desktop and VM-1. Observe the change in PowerShell and Wireshark. The "Ping" has timed out and is no longer able to go through because of the new "Inbound Security Rule" we created. Now let's go back to Azure at the Host and set the ICMP rule to "Allow". Jump back to VM-1 and observe that the ICMP traffic can once again go through to VM-2.
<p>
<p>
<img src="https://i.imgur.com/RuAe85x.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/vpp8LOL.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/lQf7yb2.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/gjMrUKA.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XWe2xEd.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ZujyaOh.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NZC1TCL.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>  
</p>
<p>
</p>
<br />
<h2>Step 8.</h2> 

**SSH Traffic** 
<p>
Clear out the traffic in Wireshark and enter "ssh" in the traffic field for this next test. We will login to our VM-2 running Linux using the Command Line in VM-1. To do this go to PowerShell and type in ssh followed by the Username and Private IP of VM-2 in this case it will look like this "ssh labuser@10.0.0.5". Next hit enter and type "yes" when it asks if "Are you are sure you want to connect". Next you will be prompted to enter it's password, type it in and hit enter again (Note for security purposes it will not show what you are typing as you enter the password, just type it correctly and it will work). You are now logged in as the User in VM-2. As you will notice, Wireshark will show all the "SSH" traffic activity as you are in the process of and after you are logged in via the command line. You can type in "exit" to logoff VM-2. 
<p>
<p>
<img src="https://i.imgur.com/lQ8mgYx.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/RtFROhM.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/7KTOtcI.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
<h2>Step 9.</h2> 

**DHCP Traffic** 
<p>
To view the DHCP protocol traffic, type in Wireshark "dhcp". DHCP is a protocol for assigning dynamic IP addresses to devices on a network. Go to PowerShell and type "ipconfig /renew" -> hit enter. This command "ipconfig /renew" gets a new DHCP address.
<p>
<p>
<img src="https://i.imgur.com/uIXbQM3.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/ijwvXca.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />
