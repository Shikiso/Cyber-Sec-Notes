# Cost Management
## Factors affecting costs
| Resource Type                                                                                                                                           | Consumption                                                                  | Maintenance                                                                                                                                                                            | Geography                                                                                                                   | Network Traffic                                                                                                                      | Subscription                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Costs are resource-specific. Meaning the usage that a meter tracks and the numbr of meters associated with a resource, depend on the resource type.<br> | With a pay-as-you-go model, consumption is one of the biggest drivers costs. | Monitoring your Azure footprint and maintaining your environment can help you identify and mitigate costs that aren’t necessary, such as shutting down underused virtual machines.<br> | The same resource type can cost different amounts depending on the geographic area, which has an impact on Azure costs.<br> | While some inbound data transfers are free, the cost for outbound data or data between Azure resources is impacted by billing zones. | The type and configuration of your subscription can also impact your cost. For example, the free trial lets you explore some Azure resources for free. |

Using tools such as the pricing calculator and Total Cost of Ownership (TCO) calculator you can estimate cost savings and help with estimating costs of products.

# Governance and Compliance
## Azure Policy
Policy helps enforce standards and to access compliance at scale. Provides governance and resource consistency with regulatory compliance, security, cost and management.

## Resource Locks
Protects your resources from accidental deletion or modification.
Manages locks at subscription, resource group or individual resource levels.

## Manage resource locks
1. Create a resource
2. Add a ReadOnly resource lock to prevent resource modification
3. Update lock and retest
4. Remove the resource lock
5. Delete the resource

# Management and Deployment Tools
Tools for interacting with Azure:
- Azure portal
- Azure PowerShell
- Azure Cloud shell
- Command-Line Interface (CLI)
Azure Arc: Extends management to on-premises, multi-cloud and edge
Azure Resource Manager: Provides management layer that enables you to modify resources
Infrastructure as code
Azure Resource Manager templates: JSON files used to create + deploy azure infrastructure without commands
Bicep

# Monitoring Tools
Azure Advisor: Analyzes deployed resources and makes recommendations based on best practices to optimize deployments
Azure Service Health: Collection of services that inform you of status, service status and impact
Azure Monitor: Collects data from applications + services and analyzes
