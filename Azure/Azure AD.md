A cloud-based identity and access management (IAM) solution that helps organizations manage user access to applications and data in the cloud and on-premises environments.

![](/Images/azure_ad.png)

# What is offered
- Build on trusted platform to advanced your organization with AI and cloud services
- Manage infrastructure, data, analytics and AI solutions

# Azure Accounts
To do anything you need an Azure subscription.
When working with your own applications and business needs you need to create an Azure account, a subscription will then created for you. Once the account is made you are free to create additional subscriptions.
![](/Images/azure_accounts.png)

# Azure infrastructure
Azure has two main groupings of core architectural components. Physical infrastructure and management infrastructure.

## Physical Infrastructure
Datacenters form the physical foundation of the Azure cloud platform. As a global cloud provider Azure has datacenters around the work. Individually these datacenters are not accessible. They are grouped into either regions or availability zones which help with reliability.
## Regions
A geographical are that contains at least one datacenters that are nearby and networked together with a low-latency network.
### Region Pairs
Most regions are paired with another within the same geography. This allows for the replication of resources across a geography that helps reduce the likelihood of interruptions.
![](/Images/region_pair.png)
Advantages of region pairs:
- If an extensive Azure outage occurs, one region out of every pair is prioritized to make sure at least one is restored as quickly as possible for applications hosted in that region pair.
- Planned Azure updates are rolled out to paired regions one region at a time to minimize downtime and risk of application outage.
- Data continues to reside within the same geography as its pair (except for Brazil South) for tax- and law-enforcement jurisdiction purposes.
### Sovereign Regions
Instances of Azure that are isolated from the main instance of Azure. You may need to use a sovereign region for compliance or legal purposes.

Sovereign regions include:
- US DoD Central, US Gov Virginia, US Gov Iowa and more: These regions are physical and logical network-isolated instances of Azure for U.S. government agencies and partners. These datacenters are operated by screened U.S. personnel and include additional compliance certifications.
- China East, China North, and more: These regions are available through a unique partnership between Microsoft and 21Vianet, whereby Microsoft doesn't directly maintain the datacenters.

## Availability Zones
Physically separate datacenters within an Azure region.
Each zone is made up of at least one datacenter.
Availability zones are set up to be an isolation boundary. Meaning if one goes down the other continues working.
![](/Images/availability_zones.png)
Availability zones are primarily used for VMs, managed disks, load balancers and SQL datbase.
Azure services that support availability zones fall into three categories:
- Zone services: You ping the resource to a specific zone
- Zone-redunant services: The platform replicates automatically across zone
- Non-regional services: Services are always available from Azure geographies.

# Management Infrastructure
This includes Azure resources and resource groups, subscriptions and accounts.

## Resources and Resource Groups
- Resource groups are grouping of resources.
- Only a single resource can be placed in a group at a time.
- Groups cannot be nested.
- When you apply a action to a resource group that action will apply to all the resources in the group.

## Subscriptions
Subscriptions are a unit of management, billing and scale.