<p align="center">
<img src="https://static.wixstatic.com/media/2ebf04_4302f0f9efbd490a84e66d0ea2a414bd~mv2.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we conduct an analysis of the different types of network traffic to and from Azure Virtual Machines using the Wireshark packet capture and analysis tool, as well as experiment with Network Security Groups.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command Prompt
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create two virtual machines: You'll need to create two virtual machines (VMs) that will serve as the traffic sources for network analysis. Use pre-built images, namely Windows 10 Pro Version 21H2 and Ubuntu Server 20.04 LTS. These VMs will communicate with each other within the same virtual network.
- Deploy Wireshark on the Windows 10 Pro VM: Once you have created the virtual machines, you will need to install the Wireshark network protocol analyzer software on the Windows 10 Pro VM. Wireshark captures and displays network traffic, allowing the user to inspect packets and analyze network behavior.
- Generate and analyze network traffic: Generate network traffic between the two VMs using various protocols such as Internet Control Message Protocol (ICMP), Secure Shell (SSH), Dynamic Host Configuration Protocol (DHCP), Domain Name System (DNS), and Remote Desktop Protocol (RDP). Capture and analyze the network traffic using Wireshark by applying filters for these protocols. This analysis will reveal important information such as source and destination IP addresses, and packet lengths, providing insights into the network's behavior and performance.

<h2>Actions and Observations</h2>

<p>
<p align="center"> 
<img width="1119" alt="Step 1" src="https://github.com/user-attachments/assets/20d1564f-9065-4e0d-830b-610e911e6e1b">
</p>
<p>
Step 1: Create a new resource group on Microsoft Azure.
</p>
<br />

<p>
<p align="center"> 
<img width="838" alt="Step 2" src="https://github.com/user-attachments/assets/3568e5d6-7e42-41b5-aa5d-a391ab5cf858">
</p>
<p>
Step 2: Set up an Azure virtual machine (VM) operating on Windows 10 Pro, Version 21H2.
</p>
<br />

<p>
<p align="center"> 
<img width="850" alt="Step 3" src="https://github.com/user-attachments/assets/317588ab-74dc-4061-ac34-6ef2474dac1e">
</p>
<p>
Step 3: Generate a username and password for the administrator account and proceed with creating the VM.
</p>
<br />

<p>
<p align="center"> 
<img width="844" alt="Step 4" src="https://github.com/user-attachments/assets/3f16511a-4396-4240-ad12-14cdb1da1ab8">
</p>
<p>
Step 4: Create an additional virtual machine that operates on Ubuntu Server 20.04 LTS. Choose a username and password for the administrator account and include it in the same resource group and virtual network as the first VM.
</p>
<br />

<p>
<p align="center"> 
<img width="1108" alt="Step 5" src="https://github.com/user-attachments/assets/8cb19371-debc-444d-a606-fa914e546d51">
</p>
<p>
Step 5: Connect to the first virtual machine using a remote desktop connection.
</p>
<br />

<p>
<p align="center"> 
<img width="857" alt="Step 6" src="https://github.com/user-attachments/assets/cf806f07-9afe-4eea-9a19-b253a878b2f8">
</p>
<p>
Step 6: Open Microsoft Edge and navigate to https://wireshark.org/download.html to download the latest version of Wireshark.
</p>
<br />

<p>
<p align="center"> 
<img width="369" alt="Step 7" src="https://github.com/user-attachments/assets/bec7d4eb-cd39-4512-96b9-9d77df1abf0d">
</p>
<p>
Step 7: Install Wireshark with the default installation settings.
</p>
<br />

<p>
<p align="center"> 
<img width="559" alt="Step 8" src="https://github.com/user-attachments/assets/3967ffc6-f3aa-43e0-a290-58b335d4bd27">
</p>
<p>
Step 8: Begin capturing packets by launching Wireshark, clicking on the Ethernet option, and selecting the Blue Wireshark icon.
</p>
<br />

<p>
<p align="center"> 
<img width="560" alt="Step 9" src="https://github.com/user-attachments/assets/41bcebed-bf3b-44cd-86ef-0d2bcd5d6d85">
</p>
<p>
Step 9: Observe the traffic and filter it for ICMP traffic.
</p>
<br />

<p>
<p align="center"> 
<img width="1100" alt="Step 10" src="https://github.com/user-attachments/assets/7487b724-7f29-48ea-a2e4-2b3b4ead7d46">
</p>
<p>
Step 10: Using Windows PowerShell, ping the private IP address of the second virtual machine running Ubuntu Server and observe the traffic.
</p>
<br />

<p>
<p align="center"> 
<img width="1100" alt="Step 11" src="https://github.com/user-attachments/assets/b484ac31-feb5-4151-a183-15e690b5d903">
</p>
<p>
Step 11: Ping the second virtual machine non-stop using the -t command. Afterwards, proceed to block ICMP traffic from Azure for virtual machine 2.
</p>
<br />

<p>
<p align="center"> 
<img width="1126" alt="Step 12" src="https://github.com/user-attachments/assets/8f273cca-22e9-4b71-b4b6-136b1d486e7f">
</p>
<p>
Step 12: Access the network security groups section, choose the second virtual machine, then navigate to Netowork, then click on "network settings", and select "SSH."
</p>
<br />

<p>
<p align="center"> 
<img width="1115" alt="Step 13" src="https://github.com/user-attachments/assets/fb590bbb-b865-4c59-babd-07a527c0529a">
</p>
<p>
Step 13: Keep the settings the same, but modify the protocol to ICMP, choose "Deny " for the action, set the priority to 299, and click on "Save"
</p>
<br />

<p>
<p align="center"> 
<img width="1100" alt="Step 14" src="https://github.com/user-attachments/assets/785112bb-cae9-4115-bf7f-ed48c99b5f88">
</p>
<p>
Step 14: Notice how ICMP traffic has come to a halt due to the adjustments we made to block it.
</p>
<br />

<p>
<p align="center"> 
<img width="1124" alt="Step 15" src="https://github.com/user-attachments/assets/b8fd99c3-fcd9-4ad7-910d-e626d7783a4c">
</p>
<p>
Step 15: Return to Inbound security rules in Azure, select "Allow" under action to enable ICMP traffic, and click on "Save".
</p>
<br />

<p>
<p align="center"> 
<img width="1100" alt="Step 16" src="https://github.com/user-attachments/assets/ca265e76-73dd-4557-8480-b0a9ca5358e6">
</p>
<p>
Step 16: Observe the resumption of replies for ICMP traffic, and then press "Ctrl + C" to stop the non-stop ping.
</p>
<br />

<p>
<p align="center"> 
<img width="1112" alt="Step 17" src="https://github.com/user-attachments/assets/3b9c9810-6595-4fb8-91d4-d514c18c44e9">
</p>
<p>
Step 17: Filter for SSH traffic, and then connect to the command line of virtual machine 2 by typing the following command into PowerShell: "ssh [username of virtual machine]@[vm2privateipaddress]. " After typing "yes," enter the password that we created for the administrator account of VM 2.
</p>
<br />

<p>
<p align="center"> 
<img width="1105" alt="Step 18" src="https://github.com/user-attachments/assets/07e855ac-1865-4741-af52-a75429b206cc">
</p>
<p>
18. Step 18: While in virtual machine 2's command line, execute the following commands and observe the SSH traffic:
<ul>
  <li>id</li>
  <li>uname -a</li>
  <li>pwd</li>
  <li>ls -lasth</li>
 </ul> 
Then, type "exit" to leave virtual machine 2's command line.
</p>
<br />

<p>
<p align="center"> 
<img width="1103" alt="Step 19" src="https://github.com/user-attachments/assets/57bc45f9-ffb9-4291-9203-c41535c50b67">
</p>
<p>
Step 19: Filter for DHCP traffic and execute the command "ipconfig /renew" in PowerShell to force DHCP to assign a new IP address, then observe the traffic.
</p>
<br />

<p>
<p align="center"> 
<img width="1102" alt="Step 20" src="https://github.com/user-attachments/assets/10845b9f-230f-4461-b620-2bdf861b7699">
</p>
<p>
Step 20: Filter for DNS traffic, and type "nslookup www.google.com" in PowerShell, then observe the DNS traffic.
</p>
<br />

<p>
<p align="center"> 
<img width="1106" alt="Step 21" src="https://github.com/user-attachments/assets/1cb25e2c-9208-4a12-8142-5a4b2fb82e92">
</p>
<p>
Step 21: Filter for Remote Desktop Protocol (RDP) traffic and observe the traffic that is already present because of our existing remote desktop connection.
</p>
<br />
