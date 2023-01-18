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

<h2>Action Steps and Observations</h2>

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

<p>
<img width="673" alt="image" src="https://user-images.githubusercontent.com/122701786/213079045-2d72982a-8bcc-4a08-b479-2064f089abf5.png">
</p>
<p>
Step 3: Observe the network you created within Network Watcher
</p>
<br />

<p>
<img width="332" alt="image" src="https://user-images.githubusercontent.com/122701786/213079148-1140a236-56d7-4b4a-b5fb-1242105837df.png">
</p>
<p>
Step 4: Remote Desktop into VMs

</p>
<br />

<p>
<img width="395" alt="image" src="https://user-images.githubusercontent.com/122701786/213079950-b37cd669-4463-4da7-b82e-c2707ee57e83.png">
</p>
<p>
Step 5: Install & Run WireShark

</p>
<br />

<p>
<img width="709" alt="image" src="https://user-images.githubusercontent.com/122701786/213082109-8c9ce448-2111-47ab-8f5e-21e5e7716387.png">
</p>

Step 6: Open Wireshark and filter for ICMP traffic only
</p>
<br />

<p>
<img width="737" alt="image" src="https://user-images.githubusercontent.com/122701786/213083862-ea1a8828-7ef3-4fc8-9721-fdb32bb8360f.png">
</p>
<p>
Step 7: Test Connectivity Between VMs. Observe your ping requests and replies within Wireshark.
  
  </p>
<br />

<p>
<img width="742" alt="image" src="https://user-images.githubusercontent.com/122701786/213084429-1b6be90f-442b-4f6f-ad84-5049c14eb849.png">
</p>

Step 8: From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark.

</p>
<br />

<p>
<img width="376" alt="image" src="https://user-images.githubusercontent.com/122701786/213086983-c550e5b4-cd90-4200-9c84-c693eb907ded.png">
</p>
<img width="394" alt="image" src="https://user-images.githubusercontent.com/122701786/213087142-7f2fc34a-e230-40b3-9d7f-dbee08674ef6.png">
<img width="343" alt="image" src="https://user-images.githubusercontent.com/122701786/213086410-68e7adab-2be7-4cc6-a808-d216ac4d398e.png">

Step 9: Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM. Try disabling incoming ICMP traffic from the Network Security Group your Ubutu uses. Then, try enabling the traffic once more.


<p>
<img width="896" alt="image" src="https://user-images.githubusercontent.com/122701786/213088378-d385ec66-a59b-4d73-9e14-9350d9ef275f.png">
</p>
<img width="893" alt="image" src="https://user-images.githubusercontent.com/122701786/213090316-833a9fda-d020-4bb8-aef9-f0d2eef6a69f.png">
<p>
  
Step 10: SSH into VM2 from VM1 via PowerShell. Type "SSH" into WireShark's filter bar (reference step 3) --> Go to "PowerShell" again, type "ssh labuser@(VM1 private IP address)" into the cmd line *view screenshot above for help --> Type "yes" to connection prompt --> enter password on next cmd line (password will not show but enter it anyway and press enter key, it will register) --> You have now successfully remotely logged into VM2's command-line Interface (CLI). It should now read "labuser@VM2:". You can type a linux cmd such as: "id" to see the new network traffic between the VMs since linking via SSH. When finished exploring, type "exit" into cmd line on PowerShell to end the connection. 
</p>
<br />

<img width="896" alt="image" src="https://user-images.githubusercontent.com/122701786/213091500-81a2e254-527b-42e1-88ad-94dd8544e1fe.png">

Step 11: Back in Wireshark, filter for DHCP traffic only. Observe the DHCP traffic appearing in Wireshark.
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig/renew). Observe the DHCP traffic appearing in Wireshark.


<p>
<img width="725" alt="image" src="https://user-images.githubusercontent.com/122701786/213091577-dd40b9b0-8496-4b24-9f2d-5f58f0c84375.png">
</p>


Step 12: Back in Wireshark, filter for DNS traffic only. From your Windows 10 VM within a command line, use nslookup to see the IP address for google.com and observe the DNS traffic.

<p>
<img width="614" alt="image" src="https://user-images.githubusercontent.com/122701786/213092040-986fec4a-43d4-4ed7-9729-d9eefe8bfdd6.png">
</p>

Step 13: Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)


Step 14: Observe the immediate non-stop spam of traffic. This traffic seems to be nonstop because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted.
