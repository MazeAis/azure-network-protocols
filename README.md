<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create a Resource Group 
- Create a Virtual Machine
- Use Wireshark to monitor network traffic for:

  - ICMP (Ping)
  - SSH (Secure Shell)
  - DHCP (IP assignment)
  - DNS (Domain lookups)
  - RDP (Remote Desktop)

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/C6ZlyVt.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create your resource group in the Azure Portal</p>
<br />

<p>
<img src="https://i.imgur.com/BNWKykA.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, set up your Windows virtual machine. Make sure all your systems are placed in the same location (called a region) so they can work together easily.

When you're creating the virtual machine:

Choose the Resource Group you made earlier. This helps keep everything organized.
Let the system create a new Virtual Network (VNet) and Subnet for you. Think of these like a private network that your virtual machine will use to communicate.
When you get to the Administrator Account section, be sure to set your username and password.
</p>
<br />

<p>
<img src="https://i.imgur.com/BIwssjc.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create an Linux virtual machine.

Choose the Resource Group you made earlier. This helps keep everything organized.
Let the system create a new Virtual Network (VNet) and Subnet for you.
When you get to the Administrator Account section, select password authentication and set your username and password.
</p>
<br />

<p>
<img src="https://i.imgur.com/LnXZ6vM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The two virtual machines were set up in Azure and placed in the same private network so they can easily communicate and share information.
</p>
<br />

<h2>Inspecting Traffic Between Virtual Machines </h2>
<h3>ICMP </h3>

<p>
<img src="https://i.imgur.com/P2sSpT3.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect to your Windows 10 virtual machine using Remote Desktop. Once you're in, install Wireshark, open it, and set the filter to show only ICMP traffic (which is used for things like ping).
</p>
<br />

<p>
<img src="https://i.imgur.com/gXms4rJ.png" height="90%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Find the private IP address of the Ubuntu virtual machine, then go to the Windows 10 virtual machine and try to ping it. Open Wireshark, make sure you're filtering for ICMP traffic, and watch the ping requests and replies appear.
</p>
<br />

<p>
<img src="https://i.imgur.com/CDLRCab.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Attempt to ping a public website such as www.google.com and use Wireshark to watch the network traffic that appears.
</p>
<br />

<h3>SSH </h3>

<p>
<img src="https://i.imgur.com/j6ZrVVY.png" height="90%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, set the filter to show only SSH traffic. Then, from your Windows 10 virtual machine, connect to your Ubuntu virtual machine using SSH and its private IP address. Once connected, type a few basic Linux commands like ls or pwd and watch the SSH traffic appear in Wireshark.
</p>
<br />

<h3>DHCP </h3>

<p>
<img src="https://i.imgur.com/OomeytU.png" height="60%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, apply a filter to show only DHCP traffic. 
Then, on your Windows 10 virtual machine, open the command line and run ipconfig /renew to request a new IP address. Watch as the DHCP traffic shows up in Wireshark.
</p>
<br />

<h3>DNS </h3>

<p>
<img src="https://i.imgur.com/PV6xlTt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, set the filter to display only DNS traffic.

Then, on your Windows 10 virtual machine, open the command line and use the `nslookup` command to find the IP addresses for `www.google.com` and `www.disney.com`. Watch the DNS traffic appear in Wireshark as the system looks up the domain names.

</p>
<br />

<h3>RDP </h3>

<p>
<img src="https://i.imgur.com/z8h4g9M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, apply a filter for RDP traffic using tcp.port == 3389.

You’ll notice a continuous stream of network activity. Since Remote Desktop is live and running, it keeps sending little bits of information back and forth—even if you're not clicking or typing. This helps keep the connection smooth and up to date. That’s why you’ll see constant traffic on `TCP port 3389` in Wireshark.

</p>
<br />

### ✅ Summary

This project demonstrates how to analyze and understand network traffic between virtual machines in Microsoft Azure using Wireshark. By setting up both Windows and Ubuntu VMs in the same virtual network, we were able to:

- Observe different types of network traffic (ICMP, SSH, DHCP, DNS, RDP)
- Use **Wireshark** to capture and filter protocol-specific traffic
- Understand how communication flows between cloud-based machines
- Gain practical experience with **Network Security Groups (NSGs)** and protocol behavior
- Learn how continuous services like RDP maintain constant traffic

Through this lab, I developed hands-on cloud networking skills, including VM provisioning, remote access, packet inspection, and troubleshooting—foundational abilities for any IT or cybersecurity role.
