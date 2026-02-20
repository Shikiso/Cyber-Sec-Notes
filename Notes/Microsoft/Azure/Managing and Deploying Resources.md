# Tools for interacting with Azure
- Azure Portal
- Azure Powershell
- Azure Command Line Interface (CLI)

# Azure Arc
Azure Arc provides a centralized way to:
- Manage your entire environment together by projecting your existing non-Azure resources into ARM.
- Manage multi-cloud and hybrid virtual machines, Kubernetes clusters, and databases as if they are running in Azure.
- Use familiar Azure services and management capabilities, regardless of where they live.
- Continue using traditional ITOps while introducing DevOps practices to support new cloud and native patterns in your environment.
- Configure custom locations as an abstraction layer on top of Azure Arc-enabled Kubernetes clusters and cluster extensions.

Outside of Azure Azure Arc can manage:
- Servers
- Kubernetes clusters
- Azure data services
- SQL Server
- Virtual machines (preview)

# Azure Resource Manager
Deployment and management service for Azure.
With Azure Resource Manager (ARM) you can:
- Manage your infrastructure through declarative templates rather than scripts. A Resource Manager template is a JSON file that defines what you want to deploy to Azure.
- Deploy, manage, and monitor all the resources for your solution as a group, rather than handling these resources individually.
- Re-deploy your solution throughout the development life-cycle and have confidence your resources are deployed in a consistent state.
- Define the dependencies between resources, so they're deployed in the correct order.
- Apply access control to all services because RBAC is natively integrated into the management platform.
- Apply tags to resources to logically organize all the resources in your subscription.
- Clarify your organization's billing by viewing costs for a group of resources that share the same tag.
## ARM Templates
ARM templates lets you describe the resources you want to use in a JSON format.