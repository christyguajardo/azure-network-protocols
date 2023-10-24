 <p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this demonstration, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, DHCP, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>
Virtual Machine Set Up: '🖥️

Step 1: Set Up Azure Virtual Machines and Network Security Groups '🚀

'🪐Create Azure Virtual Machines:
Create at least two Azure Virtual Machines to simulate network traffic. Assign them appropriate configurations and operating systems

 '🪐Virutal Machine 1 (VM1) is Windows

 '🪐Virtual Machine 2 (VM2) is Linux (Ubuntu)

'🪐Configure Network Security Groups (NSGs):
Create Network Security Groups and define inbound and outbound rules to control traffic to and from the VMs. For instance, you can allow or deny specific ports or protocols.

Step 2: Capture Network Traffic with Wireshark '🚀

'🪐Install and Configure Wireshark on VMs:

'🪐Install Wireshark on the Azure VMs you created. Ensure that it's properly configured to capture network traffic on the desired network interfaces

Step 3: Start a Capture: '🚀
Launch Wireshark on the VM and start a packet capture on the network interface

'🪐Generate Network Traffic:
Generate network traffic by accessing web pages, pinging other VMs, or using other applications that utilize the network

Step 4: Stop the Capture: '🚀

'🪐Stop the packet capture in Wireshark after capturing sufficient traffic

<h2>Actions and Observations</h2>

We are starting this demonstration as if the VMs and WireShark have already been installed. The main point of this is to display raw traffic between the VMs that have already been created in Azure. To start, paste IP address of VM1 into Remote Desktop credentials. And of course you will need to have the ip addresses for both of your VMs. You can easily get those by toggling back and forth from your Remote Desktop and your personal desktop

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/2ddb242c-9346-464b-b9f3-5126a06b942c)

 
</p>
<p>
Click on Ethernet (should turn blue)
Click on the sharkfin symbol in top left corner (capturing packets form Ethernet) 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/91896e5f-bd52-40cf-b473-08e11364f76f)


</p>
<br />

Hit Enter 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/36c47b59-213d-45be-ab0f-62277a13953d)
You are now able to see live traffic that is happening in VM1. Continuous traffic

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/21007cf1-2839-4006-8e5e-c3a649a17f15)


</p>
<p>
Type in icmp. This stops the spamming traffic. All the traffic is being filtered by icmp
ICMP is Internet control messaging protocol, which is the protocol that uses ping

 ![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/80868c06-9e02-49ce-918a-6d7c7e6b77c4)
Voila! No traffic! 

Let’s go to PowerShell! '🐚
Since we want to see traffic between VM1 and VM2, so we are going to ping it. We need the ip address for VM2 in order to ping it. So we are going back to our original desktop (go back to Azure) and copy the private ip address (10.2.0.5)

At command line type: ping 10.2.0.5

Per below, 4 packets have been sent and 4 have been received 
VM2 responded 4 times

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/d6738ffa-a3a8-4d87-baf2-910b817cbed3)


Okay for fun we are now going to ping a public website. We will ping google.com in order to see more traffic in the protocol analyzer

At command line type: ping www.google.com -4

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/f4810bf3-b4af-44b3-b154-3bd9f12df2ad)

We are sending traffic to google and google is replying. Below is a snapshot of the big picture check out the alphabet! LOL!

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/403fb260-fa8f-49f5-91c6-5a1fe43a9c74)


We are now going to initiate a perpetual/non-stop ping from VM1 to VM2
Restart the capture data in Wireshark, click on the green shark fin to clear data. Click on Continue without saving data 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/16202d13-c75d-4119-9e8c-38c555fb8909)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/9e6a97bd-c20d-445f-a445-701a2e530543)

This cleared the traffic

At command line type: ping 10.2.0.5 -t  
This will start a perpetual ping

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/24c0527d-0744-4cf0-a18f-9615affc2f7a)


Observe traffic

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/6341df58-6d22-4294-8dc9-d900ec660035)

Observe traffic

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/e819586b-e619-4299-93b0-09cfa876a6a8)


Now we are going to stop the traffic (ping)

So let's head back to Azure in order to set up firewall (this will disable ICMP traffic)

  '🪐Go to Network Security Groups – click on vm2-nsg
   
  '🪐Go to settings and select: Inbound Security Rules
  
  '🪐Click add, this will allow you to add the rule. We are going to select an * (which means any) for both Source Port Ranges & Destination Port Ranges
  
  '🪐Select Any for Source & Destination
  
  '🪐Select deny in order for the ping to stop. This will block the ICMP traffic
  
  '🪐Make sure that you number the priority prior to any/other rules in group 

This will stop traffic 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/4c33476f-ae31-4b09-b331-a61040719863)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/234c07d2-73a2-4945-8b71-b08d4bcaa017)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/5d19fd00-b3e1-4bdb-8bf8-ddb721c6d3fc)

Go back to VM1 remote desktop to see if it’s been timed out – stopped. Traffic is now getting blocked by VM2’s firewall

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/1d2c6782-2077-4e75-b845-3a9f195d3ce2)



It's now time to Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using

  '🪐Go back to Network Security Group (NSG) in Azure 

  '🪐Go to settings and select: Inbound Security Rules

  '🪐Click on rule that we made earlier in the demonstration

  '🪐Change action from deny to allow

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/712bc8ee-ea91-434b-b77b-18415baeae6a)


Click on rule that we made earlier in the demonstration (rule 200)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/bdae571a-2104-4124-a490-734250a190ee)

Change action from deny to allow

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/f57a5498-ed5d-42c8-95d3-34854c132fc0)


Click save 

We should once again see traffic in wireshark and powershell

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/77c924ad-5ce8-47dd-a5be-d142504c0f61)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/1dd8d628-7a93-4f12-aea9-25e4487006a1)

In order to stop the ping activity, at command line type: control-c 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/e79ec045-a4b7-41b4-9cae-9acd4a277e51)





Next we are going to filter for SSH Traffic. (SecureShell)
From Windows VM SS

In Powershell: 

At command line type: ssh username@privateipaddressof VM2  
In this case, at command line type: ssh labuser@10.2.0.5

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/0af0d708-064e-4e51-a239-9765dd8669bd)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/3c687b36-916d-4ffe-bdcd-2dbcc503e855)

Next, in order to stop observing traffic, at command line type: exit 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/9205a8d3-4fa2-4fdd-b910-21440a840d26)


Next we are going to filter for DHCP Traffic 

DHCP is used to automatically assign an ip address

Go to wireshark 

Filter/type in DHCP

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/fcb9b77a-4f52-402b-8467-21714297bb0c)

Type in ipconfig /renew – now observe traffic. We got our ip address reissued to us, see powershell printscreen

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/e395ba5b-8178-4f54-a562-af0cc03e2adf)


Observe traffic

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/3fce9d9e-58f7-4123-869a-60bb12dfb62d)


To observe traffic for DNS 
Powershell:  

At command line type: nslookupwww.google.com 
Also at next command line type: nslookupwww.disney.com 

We are now able to observe Disney and Google traffic 

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/d88eea5a-2d53-4245-9da4-a70dfc021488)

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/bec9bc71-81bb-41ab-8299-cce7f6ee61d6)


To observe traffic for RDP

![image](https://github.com/christyguajardo/azure-network-protocols/assets/147533626/29243ac8-f073-453b-b8ff-896c36cdc120)

This concludes this demonstration. Thank you!
 
</p>
<br />


