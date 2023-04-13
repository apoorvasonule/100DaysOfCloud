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

✍️ Add a mini tutorial to encourage the reader to get started learning something new about the cloud.

### Step 1 — Summary of Step

![Screenshot](https://via.placeholder.com/500x300)

### Step 1 — Summary of Step

![Screenshot](https://via.placeholder.com/500x300)

### Step 3 — Summary of Step

![Screenshot](https://via.placeholder.com/500x300)

## ☁️ Cloud Outcome

✍️ (Result) Describe your personal outcome, and lessons learned.

## Next Steps

✍️ Describe what you think you think you want to do next.

## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
