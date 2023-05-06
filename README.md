<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP traffic
- Observe SSH traffic
- Observe DHCP traffic 
- Observe DNS traffic 
- Observe RDP traffic 

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/w1o33aX.png" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Observe ICMP Traffic
<br>
-Use Remote Desktop to connect to your Windows 10 Virtual Machine
<br>
-Within your Windows 10 Virtual Machine, Install Wireshark
<br>
-Open Wireshark and filter for ICMP traffic only
<br>
-Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
<br>
-Observe ping requests and replies within WireShark
<br>
-From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
<br>
-Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
<br>
-Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
<br>
-Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
<br>
-Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
<br>
-Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
<br>
-Stop the ping activity

</p>
<br />

<p>
<img src="https://i.imgur.com/13bBJui.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Observe SSH Traffic
<br>
-Back in Wireshark, filter for SSH traffic only
<br>
-From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
<br>
-Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
<br>
-Exit the SSH connection by typing ‘exit’ and pressing [Enter]

</p>
<br />

<p>
<img src="https://i.imgur.com/SjcOoXK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Observe DHCP Traffic
<br>
-Back in Wireshark, filter for DHCP traffic only
<br>
-From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
<br>
-Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/0RA5Vci.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Observe DNS Traffic
<br>
-Back in Wireshark, filter for DNS traffic only
<br>
-From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
<br>
-Observe the DNS traffic being show in WireShark
</p>
<br />

<p>
<img src="https://i.imgur.com/T1UNkXQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. Observe RDP Traffic
<br>
-Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
<br>
-Oserve the immediate non-stop spam of traffic. This is occuring because we are using Remote Desktop Protocol to connect to our virtual machines.
<br>
-Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
</p>
<br />
