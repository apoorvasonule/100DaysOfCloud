# Create Virtual Network in Azure

## Introduction

To create a virtual network in Azure, then create two virtual machines (VMs) in the network, deploy Azure Bastion to securely connect to the VMs from the internet, and communicate privately between the VMs.


## Prerequisite
- Azure subscription

Knowledge about networking
- https://devblogs.microsoft.com/premier-developer/understanding-cidr-notation-when-designing-azure-virtual-networks-and-subnets/
- https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/1-introduction


## Cloud Research
- **How many IP addresses does Azure hold per subnet?**
The number of IP addresses that Azure can hold per subnet depends on the address space and the subnet mask that you define for the subnet.
For example, if you define a subnet with an address space of 10.0.0.0/24, the subnet mask is 255.255.255.0, which means that the subnet can hold up to 256 IP addresses. Azure holds 5 IP addresses for every subnet. The first and last IP in each subnet is reserved for the network identification and for broadcast, respectively. Azure also holds 3 additional addresses for internal use starting from the first address in the subnet. So, this leave 256-5 = 251 usable IP addresses.

- **What is the smallest IP address range you can specify for an Azure subnet?**
The smallest IP address range you can specify for an Azure subnet is a /29 prefix, which provides a total of 8 IP addresses, with 3 usable addresses after accounting for the network, internal use, and broadcast addresses.

- **In this IP range 10.1.0.0/29 what does the number after the slash represent?**
The number after the slash represents the subnet mask.

- **Can a subnet be deleted from a virtual network?**
Yes, a subnet can be deleted from a virtual network. It's important to note that deleting a subnet will also delete all resources that are associated with that subnet, such as virtual machines or network interfaces. Also, if a subnet is associated with a network security group, you will need to remove the association before you can delete the subnet.

- **Can changes be made to an IP address range?** 
Yes, changes can be made to an IP address range in Azure. It can be changed by updating the virtual network configuration. To do so, you need to go to the virtual network settings in the Azure portal or use the Azure CLI or PowerShell. Then, you can modify the IP address range and save the changes. However, it's important to note that changing the IP address range of a virtual network can affect the IP addresses of all the resources within that virtual network, and may require to reconfigure the IP addresses of virtual machines and network interfaces.


## Try yourself

### Step 1 — Create a Resource Group
- Go to azure portal and serach for resource group.
- Click on the result and create a resource group.
- Give it a name and location and hit create.
<img width="475" alt="image" src="https://user-images.githubusercontent.com/75572990/232022961-ea2f4709-9519-4232-9b40-112f41566bfb.png">



### Step 2 — Create a Virtual Network
- Search Virtual Network and select it.
- Select Resource group created in step 1.
- Give name for virtual network and region.
- Go to IP address tab, Check if default ip address under Add an IP address space is 10.0.0.0/16. If not, select the garbage can icon to remove any address space that already appears, and then enter 10.0.0.0/16.
- Click add subnet and give name as default and address range as 10.0.0.0/24.
- On security tab, enable azure bastion.
- Review + create
<img width="278" alt="image" src="https://user-images.githubusercontent.com/75572990/232026200-60356f65-828c-4e66-8654-6c0a73a0388d.png">



### Step 3 — Create Virtual Machines
- Create 2 VMs in the virtual network created in step 2.
- Search for virtual machine and select it.
- Give name for VM, same region as virtual network, image as windows server 2019 datacenter.
- Give administrator accounts details.
- Go to networking tab, select the virtual network and subnet created in step 2.
- leave rest as default and hit review+create.
- repeat these steps for VM 2.



### Step 4 — Connect to VMs
- On virtual machine page, at the top click connect.
- Select RDP and download the file or select bastion.
- Give credentials for VMs and connect.



### Step 5 — Communicate between VMs
- From VM1, open powershell.
- We have to allow ICMP(Internet Control Message Protocol) to make connection between VM1 and VM2.
- enter the following command to allow ICMP.
``New-NetFirewallRule –DisplayName "Allow ICMPv4-In" –Protocol ICMPv4``
- Open VM2 and open powershell and give following command
``ping VM1``
- This will be the output. 
<img width="480" alt="image" src="https://user-images.githubusercontent.com/75572990/232047223-4a77b1ef-0de2-458b-94be-ef4818dbb422.png">



## Social Proof

https://www.linkedin.com/posts/apoorva-sonule-07523317b_100daysofcloud-azure-azurecommunity-activity-7052623478457323521-86vD?utm_source=share&utm_medium=member_desktop
