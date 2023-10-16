 <p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

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
Virtual Machine Set Up: '🖥️

Step 1: Set Up Azure Virtual Machines and Network Security Groups '🚀

'🪐Create Azure Virtual Machines:
Create at least two Azure Virtual Machines to simulate network traffic. Assign them appropriate configurations and operating systems.

'🪐Configure Network Security Groups (NSGs):
Create Network Security Groups and define inbound and outbound rules to control traffic to and from the VMs. For instance, you can allow or deny specific ports or protocols.

Step 2: Capture Network Traffic with Wireshark '🚀

'🪐Install and Configure Wireshark on VMs:

'🪐Install Wireshark on the Azure VMs you created. Ensure that it's properly configured to capture network traffic on the desired network interfaces.

Step 3: Start a Capture: '🚀
Launch Wireshark on the VM and start a packet capture on the network interface.

'🪐Generate Network Traffic:
Generate network traffic by accessing web pages, pinging other VMs, or using other applications that utilize the network.

Step 4: Stop the Capture:
Stop the packet capture in Wireshark after capturing sufficient traffic.

<h2>Actions and Observations</h2>

How to set up Virtual Machines '🖥️

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/0ee63b19-6df7-4ac6-a36a-3a697418cf64)


 
</p>
<p>
Log into Microsoft Azure Portal and click on Virtual Machines. 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/c9b40b26-ae27-4e25-8c58-6de741de25b9)
</p>
<br />

Click on Create 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/d319ff54-bfe4-4101-a90f-429bf3e59bfc)
![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/feb7ec24-2105-4226-8401-69adb1f38ba1)

</p>
<p>
Complete all of the required fields, which are designated with an asterik. This only includes the first screen under the basic tab. 
Continue to click through the tabs then create on the last tab. Virtual Machine should be validated and deployed. 
</p>
<br />


