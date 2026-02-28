<p align="center">
<img width="650" height="180" alt="wireshark" src="https://github.com/user-attachments/assets/d0e0f94b-00b7-4dad-8a02-8a5517a4b3b0" />
</p>
 
<h1>Firewall (NSG) Configuration & Observing Network Traffic</h1>

<h2>About this Project</h2>
In this project we will configure the Network Security Group and observe traffic between Azure Virtual Machines using Wireshark.

<h2>Environment & Technology Used</h2>

- Azure Virtual Machine (Windows & Linux)
- Remote Desktop
- ICMP, SSH, DNS, RDP, HTTP/HTTPS
- Wireshark

<h2>Prerequisites</h2>
In Azure, create the following: 

- Resource Group
- Windows Virtual Machine
- Ubuntu VM
- Virtual Network & Subnet

>[!NOTE]
>_Please refer to  [MS Azure Virtual Machines](https://github.com/pmaglana/azure-active-directory) for detailed instruction on how to create VMs._</br>
>_Ensure both Virtual Machines are in the same Virtual Network / Subnet._
      

<h2>Getting Started</h2>

<h3>Observing ICMP Traffic</h3>

1. After deploying your Virtual machines in Azure, Let's use Remote Desktop to connect to your Windows Virtual Machine.
2. Within your Windows Virtual Machine, Install [Wireshark](https://www.wireshark.org)
3. Open Wireshark and start packet capture
4. Within Wireshark, filter for ICMP traffic only
5. Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows VM.
   
   a. Observe ping requests and replies within WireShark

6. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

<h3>Configuring a Firewall [Network Security Group]</h3>

1. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

   a. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic.
   
   b. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity.

   c. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM.

   d. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM.

   e. Stop the ping activity.
   
<h3>Observe DHCP Traffic</h3>

1. Back in Wireshark, filter for DHCP traffic only.
2. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line

   a. Open PowerShell as admin and run: ipconfig /renew.
   
   b. Observe the DHCP traffic appearing in WireShark.

<h3>Observe DNS Traffic</h3>

1. Back in Wireshark, filter for DNS traffic only.
2. From your Windows VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are.

   a. Observe the DNS traffic being show in WireShark.

<h3>Observe RDP Traffic</h3>

1. Back in Wireshark, filter for RDP traffic only (tcp.port == 3389).
2. Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
   
   - This is because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

   
<h2>Finishing Up</h2>
<h3>Congratulations for completing this activity.</h3>

<sub>*For questions and conerns, please reach out to paulo@maglana.com*</sub>





