# Create an Azure Policy

## Introduction
Create a policy assignment to identify non-compliant resources via the Azure portal


## Prerequisite and References
- Azure Subscription
- Knowledge about Azure Policy
  - https://docs.microsoft.com/en-us/azure/governance/policy/
  

## Cloud Research
- **What is Azure Policy?**
  Azure Policy is a service in Microsoft Azure that allows you to create, assign, and manage policies for your Azure resources. Policies are rules that enforce certain settings or actions,such as requiring certain resource tags, enforcing network security group rules, specifying allowed virtual machine SKUs, ensuring compliance with specific regulatory requirements, and more, within your Azure environment.

- **Use cases of azure policy.** 
  - Compliance: Azure Policy can ensure that your resources are compliant with industry standards, regulations, or internal policies.
  - Resource management: Azure Policy can help you manage and control the creation and use of resources in your Azure environment.    
  - Security: Azure Policy can enforce security controls and best practices for your Azure environment.
  - Governance: Azure Policy can help you establish and enforce policies for resource tagging, naming conventions, and more.
  - Cost management: Azure Policy can help you optimize costs by enforcing policies for resource size, region, and other factors that impact pricing.
  - DevOps: Azure Policy can help you integrate governance and compliance requirements into your DevOps processes by automating policy enforcement and remediation.
  - Customization: Azure Policy allows you to create custom policy definitions to enforce policies specific to your organization's needs.

- **What does the term 'scope' refer to?**
  Scope in Azure Policy refers to the extent or level at which a policy is applied within an Azure environment. Azure Policy provides different levels of scope to allow you to apply policies to specific areas of your environment, depending on your organizational requirements.
Here are the different levels of scope in Azure Policy:
  - Management group: Policies applied at the management group scope are inherited by all subscriptions and resources within that management group.
  - Subscription: Policies applied at the subscription scope apply to all resources within that subscription.
  - Resource group: Policies applied at the resource group scope apply to all resources within that specific resource group.
  - Resource: Policies applied at the resource scope apply to a specific resource within an Azure environment.

- **How many policy definitions can you have per scope?**
  The maximum number of policy definitions that you can have per scope in Azure Policy depends on the level of scope you are working with. Here are the limits:
  - Management group: Up to 2,000 policy definitions can be assigned to a single management group.
  - Subscription: Up to 500 policy definitions can be assigned to a single subscription.
  - Resource group: Up to 500 policy definitions can be assigned to a single resource group.
  - Resource: Up to 1 policy definition can be assigned to a single resource.

- **What is an initiative definition?**
  An initiative definition in Azure Policy is a collection of policy definitions that are grouped together to achieve a specific goal or objective. An initiative definition provides a way to simplify the assignment and management of policy definitions by grouping them into a single unit.


## Try yourself
In this practical, we have to create a policy assignment and assign the *Audit VMs that do not use managed disks* policy definition.

### Step 1 — Create test VMs
- Create Resource Group.
- Create 2 VMs in this resource group.
- Create 1st VM with managed disk.
- Create 2nd VM without managed disk. 

### Step 2 — Create a policy assignment
- In all services, search and select azure **policy**.
- On left side of azure policy page under Authoring, select **Assignents**.
- On the top of Assignment page, select **Assign Policy**.
- In scope, Select the subscription and resource group. 
<img width="431" alt="image" src="https://user-images.githubusercontent.com/75572990/232314655-8f19ef42-1672-4a67-91d5-95dd2758262a.png">

- Leave exclusion blank.
- Under Basics, in Policy definition, search *Audit VMs that do not use managed disks* and select it and add.
  <img width="470" alt="image" src="https://user-images.githubusercontent.com/75572990/232314832-8f76c625-f5c3-4129-9f1c-37c7160e7e9b.png">
- Give Assignment name and description. 
- Click next till Non-compliance message tab appears.
- Give message as *Virtual machines should use a managed disk*. and click next.
- Review + create

### Step 3 — Identify non-compliant resources
-Select Compliance in the left side of the page. Then locate the Audit VMs that do not use managed disks policy assignment created in step 1.
<img width="956" alt="Screenshot 2023-04-16 193045" src="https://user-images.githubusercontent.com/75572990/232316502-69d7569a-c05e-4186-8749-8399c7882a2d.png">

-If there are any existing resources that aren't compliant with this new assignment, they appear under Non-compliant resources.
<img width="929" alt="image" src="https://user-images.githubusercontent.com/75572990/232316696-1f663883-2802-44d6-b579-e447694a2549.png">



## Social Proof

https://www.linkedin.com/feed/update/urn:li:share:7053368465105063936/

