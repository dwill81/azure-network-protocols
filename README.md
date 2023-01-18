<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)
- PowerShell (Command-Line Interface)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Installation Steps</h2>

- Step 1: Create a Resource Group
- Step 2: Create Virtual Machines
- Step 3: Remote Desktop into VMs
- Step 4: Install & Run WireShark
- Step 5: Test Connectivity Between VMs
- Step 6: Alter Network Security Group Settings
- Step 7: SSH into VM
- Step 8: Observe DHCP Traffic

<h2>Actions and Observations</h2>

<p>
<img width="590" alt="image" src="https://user-images.githubusercontent.com/122701786/213075915-97868c0b-35f4-446f-9d50-c6cacb9e0b16.png">
</p>
Step 1: Create a resource group 
<p>
</p>
<br />

<p>
<img width="893" alt="image" src="https://user-images.githubusercontent.com/122701786/213077328-eb09a18d-b6b7-4115-9013-10930c0817ae.png">
</p>
<br />Step 2: Create two Vitrual Machines in Azure: Log into the Microsoft Azure Portal with your Microsoft Account --> search "Virtual Machines" in the search bar --> "create" two Virtual Machines with the following OS: Windows 10 OS for VM1 & Ubuntu OS for VM2) --> Make sure both VMs are in the same "resource group". *When setting up the VMs remember the username and password that you use. You'll need this information later to remote desktop into the VMs.*
</p>
<br />
