Not much to know just that they charge you, and to plan what the VM is for.
# Availability Sets
logical feature you can use to ensure a group of related VMs are deployed together.

## Characteristics:
- All virtual machines in an availability set should perform the identical set of functionalities.
    
- All virtual machines in an availability set should have the same software installed.
    
- Azure ensures that virtual machines in an availability set run across multiple physical servers, compute racks, storage units, and network switches.
    
- If a hardware or Azure software failure occurs, only a subset of the virtual machines in the availability set are affected. Your application stays up and continues to be available to your customers.
    
- You can create a virtual machine and an availability set at the same time.
    
- A virtual machine can only be added to an availability set when the virtual machine is created. To change the availability set for a virtual machine, you need to delete and then recreate the virtual machine.
    
- You can build availability sets by using the Azure portal, Azure Resource Manager (ARM) templates, scripting, or API tools.
    
- Microsoft provides robust Service Level Agreements (SLAs) for Azure virtual machines and availability sets. For details, see [SLA for Azure Virtual Machines](https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_9/).

# Update & Fault Domains
Used to maintain high availability and fault tolerance when deploying and upgrading applications.
