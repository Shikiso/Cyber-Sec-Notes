# Configure Just-in-time Administration
- Enable JIT for VMs through the Microsoft Defender for Cloud
- Define network ports
- Microsoft Defender for Cloud imposes a deny all inbound traffic rule for your selected ports by using NSG and Azure firewall rules
- JIT is a paid feature of Microsoft defender for cloud

# Manage Windows Virtual Machines with Azure Bastion
Azure Bastion provides secure RDP and SSH connectivity to all the VMs in the same VNet or peered VNets.

Bastion host servers:
- Are designed and configured to withstand attacks
- Provide RDP and SSH connectivity to your Azure workloads behind the bastion
(Only the Bastion requires a public IP, not the VMs its protecting)

**Use the following procedure to connect to a Windows VM using Azure Bastion**
1. Navigate to the VM which you want to connect
2. Select the VM and on the virtual machine blade select Connect
3. In the Connect drop-down list select Bastion
4. Enter the credentials of a user with appropriate permissions and the select Connect