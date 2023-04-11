<img width="504" alt="image" src="https://user-images.githubusercontent.com/75572990/231268411-ea533e7f-86cf-4258-ac93-fb8004cb9d38.png">

# Create an Azure File Share system

## Introduction

Create an Azure Files share, mount it on two virtual machines in separate availability zones in the same region, and access a text file from one instance to the other.

## Prerequisite
Knowledge about following things will help. Click on the links and learn more.
- Azure File Share : https://learn.microsoft.com/en-us/azure/storage/files/storage-files-introduction
- Azure Virtual Machines : https://learn.microsoft.com/en-us/training/modules/intro-to-azure-virtual-machines/
- Azure Storage : https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction

## Cloud Research

- I read documents which are given prerequisites.

## Try yourself

### Step 1 — Create storage account
- Create Resource Group
- Create one storage account. 
- Keep the performance as standard and Redundancy as Locally Redundant Storage.
- hit review+create.
<img width="557" alt="image" src="https://user-images.githubusercontent.com/75572990/231249025-f8f3d4ca-9374-4965-8cf2-65e1099fc089.png">


### Step 2 — Create File share
- Click on the Storage account made in previous step.
- In left side menu, under Data Storage, click on File Shares.
- click +File share and give it a name 
<img width="477" alt="image" src="https://user-images.githubusercontent.com/75572990/231251411-252edb40-4ac0-48d0-9c08-58f370e55f75.png">


### Step 3 — Create 2 Virtual Machines in Same Region, but different Availability Zone.
- Search for Virtual Machine in search bar.
- Fill in necessary information. Make note of the Region that is selected for VM as it has to be same for 2nd VM also.
- In availability options, choose availability zone.
- In availability zone, choose zone 1 for 1st VM and Image of your choice. 
- Give Administor account details.
- Hit review +create.
- Do the same step for creating second VM. Just make sure to select Zone 2 in avalibility zone field. 

<img width="479" alt="image" src="https://user-images.githubusercontent.com/75572990/231252503-d0b321af-8a1f-4a8f-919b-d55277539dd6.png">


### Step 4 — Mount Azure file share on Virtual Machines
- Click on VM1 and in overview section, at top click connect, download RDP file or use bastion.
- Give username and password to access the virtual machine.
- Once logged in, go to file Explorer, then to This PC.
- on top, click on connect, then on Map network drive and then map network drive again.
- Here we have to give drive and folder path. By default Drive is selected. If not, select a drive which is not in use. 
- For folder path, go to file share again from storage account.
- On top, click connect.
- Select windows or linux, VM operating system
- click on show script and copy the UNC path as shown in the picture below.
- <img width="383" alt="image" src="https://user-images.githubusercontent.com/75572990/231256502-7780a5dc-2dfb-4945-be11-22e564dfea76.png">
-Paste this path in folder field in the VM1 and enable Connect using different Credentials. Click Finish.
- Dashboard for network credentials will appear. In username, enter storage account name and in password, copy the password from the same script of file share we used for UNC path and paste it.
- <img width="395" alt="image" src="https://user-images.githubusercontent.com/75572990/231257296-98a44ab1-876d-4746-a86b-7989d6f953e6.png">
- You can also get this username and password in access key section in storage account.
- Do the same steps in VM2.



### Step 5 — Create a Text document in the FileShare drive in VM1 and See if it is reflecting in VM2 as well.
- In VM1, Go to the fileshare drive created in previous step.
- Make a new text document there and save it.
- Open VM2 and check the fileshare drive to see if the same file is present there or not.
- <img width="960" alt="image" src="https://user-images.githubusercontent.com/75572990/231264440-5fec9041-a719-40f5-b4d8-fa8d901a671d.png">


## Social Proof

https://www.linkedin.com/feed/update/urn:li:share:7051620032765718528/
