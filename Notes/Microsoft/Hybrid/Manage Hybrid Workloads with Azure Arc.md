# Azure Arc
A service that provides a set of technologies for organizations.
Provides a centralized, unified and self-service approach to managing:
- Windows/Linux Server
- Kubernetes clusters
- Azure Data Services

**Azure Arc Capabilities:**
- Azure Machine Configuration
- Support for resources-context-access Log Analytics data
- Microsoft Defender for Cloud
- Microsoft Sentinel
- Azure Monitor
- Azure Update Manager

# Onboard Windows Server Instances
**Deploy Azure Arc to on-premises computers and hybrid cloud computers**
1. Must have the correct permissions as administrator
	- Member of the Azure Connect Machine Onboarding role
	- Member of the Azure Connected Resource Administrator role
2. Install the Azure Connected Machine agent on each of the OS targeted for Azure Resource Manager-based management
3. Manage the onboarding of Windows Server instances from Azure Arc

# Use Azure Arc to manage Windows Server instances

| Extension                      | Additional information                                                       |
| ------------------------------ | ---------------------------------------------------------------------------- |
| CustomScriptExtentsion         | Downloads and executes scripts on Azure VMs                                  |
| Azure Key Vault                | Provides automatic refresh of certificates stored in an Azure key vault      |
| Azure Monitor Agent            | Collect monitoring data from guest operating systems of Azure and hybrid VMs |
| Azure Extension for SQL Server | Initiates a SQL Server connection to Azure                                   |
## Manage Azure Policy
- Azure Policy – service that can help organizations manage and evaluate compliance.
- Uses declarative rules based on properties of target Azure resource types.
- Azure Arc lets you to extend some capabilities of Azure Policy to operating systems of computers running in on-premises datacenters or hosted by third-party cloud providers.

## Azure Policy functionality can be grouped into four main categories:
- Enforcing compliance when provisioning new Azure resources
- Auditing compliance of existing Azure resources
- Remediating non-compliance of existing Azure resources
- Auditing compliance of the OS, application configuration, and environment settings within Azure VMs 

## Assign Azure Arc policies
- In Azure portal, navigate to Azure Arc, and then Manage servers
- Select the appropriate server, and then select Policies.
# Restrict Access to VM with RBAC
**Five available tabs on the Access control (IAM) page:**
- Check access
- Role assignments
- Deny assignments
- Classic administrators
- Roles