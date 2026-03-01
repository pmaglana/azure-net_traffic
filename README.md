<p align="center">
<img width="650" height="180" alt="wireshark" src="https://github.com/user-attachments/assets/d0e0f94b-00b7-4dad-8a02-8a5517a4b3b0" />
</p>
 
<h1>Firewall (NSG) Configuration & Observing Network Traffic</h1>

<h2>About this Project</h2>
In this project we will configure the Network Security Group and observe traffic between Azure Virtual Machines using Wireshark. You are also expected to be knowledgeable in Azure Virtual machines deployment and must be familiar with installing Softwares(WiresharK).

<h2>Environment & Technology Used</h2>

- Azure Virtual Machine (Windows & Linux)
- Remote Desktop
- ICMP, SSH, DNS, RDP, HTTP/HTTPS
- Wireshark

<h2>Prerequisites</h2>

- Resource Group
- Windows Virtual Machine
- Ubuntu Virtual Machine (Authentication type: Username & Password)
- Virtual Network & Subnet

>[!NOTE]
>_Please refer to  [MS Azure Virtual Machines](https://github.com/pmaglana/azure-active-directory) for detailed instruction on how to create VMs._</br>
>_Ensure both Virtual Machines are in the same Virtual Network & Subnet._
      

<h2>Getting Started</h2>

<h3>Observing ICMP Traffic</h3>

1. After deploying your Virtual machines in Azure, connect to your Windows VM via Remote desktop.
2. Within your Windows Virtual Machine, Install [Wireshark](https://www.wireshark.org)
3. Open Wireshark and start packet capture
4. Within Wireshark, filter for ICMP traffic only
5. Retrieve the Private IP address of the Linux/Ubuntu VM and attempt to ping it from within the Windows VM.

   <img width="1875" height="627" alt="icmp5" src="https://github.com/user-attachments/assets/8f576c4d-7e5a-432f-a75e-7eea54093038" />

   a. Observe ping requests and replies within WireShark

   <img width="1271" height="756" alt="icmp5a" src="https://github.com/user-attachments/assets/cc65bff9-5d5e-4a9f-80c1-43158a93edd3" />

6. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

   <img width="1156" height="728" alt="icmp6" src="https://github.com/user-attachments/assets/f8fa97b9-509f-401c-a625-310d6bb9590c" />

<h3>Configuring a Firewall [Network Security Group]</h3>

1. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM.

<img width="454" height="464" alt="nsg1" src="https://github.com/user-attachments/assets/5742dff8-7c34-46d7-b83c-a60414e6990b" />

   a. Go back to Azure portal, under Networking > Network settings > Network security group, click vmLinux-nsg, under settings, click inbound security rules then click the + sign to add rules. Follow the settings showing below.

   <img width="1687" height="519" alt="nsg2" src="https://github.com/user-attachments/assets/ac9421aa-0d45-4edc-b247-f7194ab52489" />
   <img width="1690" height="856" alt="nsg3" src="https://github.com/user-attachments/assets/b2ea7d75-b73d-418e-be1a-04b84af31821" />

   b. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity.

   Before:
   
   <img width="454" height="574" alt="nsg5" src="https://github.com/user-attachments/assets/7f9a05b0-c72c-46d2-9a39-1a00c117ffd0" />

   After adding security rule:

   <img width="454" height="574" alt="nsg5" src="https://github.com/user-attachments/assets/75b71072-ba11-4956-9a85-28a128365fba" />
   
   c. Re-enable ICMP traffic for the Network Security Group in Ubuntu VM. Observe the ICMP traffic in WireShark and the command line Ping activity (should start working)

   <img width="450" height="411" alt="nsg6" src="https://github.com/user-attachments/assets/eb3cf4dd-5b89-4fea-bf7f-c3113484cc40" />

   e. Stop the ping activity.

<h3>Observe SSH Traffic</h3>

1. Log back into the windows-vm, open Wireshark, start a packet capture up and filter for SSH Traffic only.
2. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
   
   a. Open PowerShell, and type: ssh labuser@(private IP address).
   
   b. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
   
   c. Exit the SSH connection by typing ‘exit’ and pressing [Enter]

   <img width="1767" height="752" alt="azure-ssh" src="https://github.com/user-attachments/assets/69f73f11-09c7-443d-b24a-7182d923cd66" />

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
   
   <img width="940" height="758" alt="azure-rdp" src="https://github.com/user-attachments/assets/5d55cdd6-7116-4584-9a5f-a39d0cf7227a" />

   RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

   
<h2>Finishing Up</h2>
<h3>Congratulations for completing this activity.</h3>

<sub>*For questions and conerns, please reach out to paulo@maglana.com*</sub>





