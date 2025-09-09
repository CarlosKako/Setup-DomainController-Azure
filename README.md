
<p align="center">
<img width="1000" height="342" alt="image" src="https://github.com/user-attachments/assets/71a7bff3-37ea-4de4-a8a0-fc9d4e841a52" />


</p>

<h1>Active Directory within Microsoft Azure Setting up a Domain Controller and Client in Azure</h1>

Welcome! In this session, we’ll set up a Domain Controller in Azure by creating DC-1 on Windows Server 2022 with a static private IP, then configure Client-1 on Windows 10 to use DC-1 as its DNS server, verify connectivity with a ping, and confirm DNS resolution through ipconfig.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Before we begin setting up the Domain Controller in Azure, make sure you have an active Azure subscription, access to the Azure portal, and permissions to create resource groups, virtual networks, and virtual machines. You should also be familiar with basic networking concepts like IP addresses and DNS, and ensure that you can RDP into Windows VMs for configuration.</h2>

</p>
<br />

<p>


<img width="1916" height="559" alt="image" src="https://github.com/user-attachments/assets/c58f8b9b-01ff-4d88-b83f-51c6e4e5cc98" />


</p>
<p>
Create a Resource Group

Go into the Azure portal, create a new resource group. This will hold all of our lab resources in one place.

Create a Virtual Network and Subnet

Within the resource group, create a Virtual Network (VNet).

Add a subnet—this is where our machines will sit and communicate with each other.

Create the Domain Controller VM

Create a Windows Server 2022 VM and name it DC-1.

Use the login credentials:

Username: labuser

Password: Cyberlab123!

Place it in the resource group and VNet we just made.

Configure the NIC Private IP

Once the VM is created, go into the Networking tab for DC-1’s NIC.

Set the private IP address to static. This prevents the IP from changing, which is critical for DNS and domain functions.

Login and Configure DC-1

Remote Desktop into DC-1.

Open Windows Defender Firewall settings and disable the firewall (just for lab connectivity testing).


</p>
<br />

<p>
<img width="860" height="732" alt="image" src="https://github.com/user-attachments/assets/4d1ca51e-e836-421f-bf1e-cf0c13f70ac0" />


</p>
<p>
Setup Client-1 in Azure

Create the Client VM

Create a Windows 10 VM named Client-1.

Use the same login credentials:

Username: labuser

Password: Cyberlab123!

Place it in the same region and Virtual Network as DC-1.

Configure DNS Settings

Once Client-1 is created, go to its Networking settings in the Azure portal.

Change the DNS server to DC-1’s private IP address.

Restart Client-1 from the portal so the DNS change applies.

Test Connectivity

Log into Client-1 with RDP. Open Command Prompt or PowerShell. Ping DC-1’s private IP address. The ping should succeed, showing the two machines are talking over the private network. Verify DNS Settings On Client-1, open PowerShell and run:

ipconfig /all

Scroll down and check the DNS server field. You should see DC-1’s private IP address listed.
