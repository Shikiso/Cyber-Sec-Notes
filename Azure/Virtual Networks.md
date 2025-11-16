Some characteristics of virtual networks in Azure:
- An Azure virtual network is a logical isolation of the Azure cloud resources.
- You can use virtual networks to provision and manage virtual private networks (VPNs) in Azure.
- Each virtual network has its own Classless Inter-Domain Routing (CIDR) block and can be linked to other virtual networks and on-premises networks.
- You can link virtual networks with an on-premises IT infrastructure to create hybrid or cross-premises solutions, when the CIDR blocks of the connecting networks don't overlap.
- You control the DNS server settings for virtual networks, and segmentation of the virtual network into subnets.

# Subnets
Provide a way for you to implement logical divisions within your virtual network.
## Some things to know about subnets are:
There are certain conditions for the IP addresses in a virtual network when you apply segmentation with subnets.
- Each subnet contains a range of IP addresses that fall within the virtual network address space.
- The address range for a subnet must be unique within the address space for the virtual network.
- The range for one subnet can't overlap with other subnet IP address ranges in the same virtual network.
- The IP address space for a subnet must be specified by using CIDR notation.
- You can segment a virtual network into one or more subnets in the Azure portal. Characteristics about the IP addresses for the subnets are listed.

For each subnet, Azure reserves five IP addresses.

|Reserved address|Reason|
|---|---|
|`192.168.1.0`|This value identifies the virtual network address.|
|`192.168.1.1`|Azure configures this address as the default gateway.|
|`192.168.1.2` _and_ `192.168.1.3`|Azure maps these Azure DNS IP addresses to the virtual network space.|
|`192.168.1.255`|This value supplies the virtual network broadcast address.|
# Addressing
You can create a public IP (idk why there is page saying this but ok).
A public ip address resource can be associated with virtual machine network interfaces. Your address can be dynamic or static.

# Peering
- There are two types of Azure Virtual Network peering: _regional_ and _global_.
- **Regional virtual network peering** connects Azure virtual networks that exist in the same region.
- **Global virtual network peering** connects Azure virtual networks that exist in different regions.
- You can create a regional peering of virtual networks in the same Azure public cloud region, or in the same China cloud region, or in the same Microsoft Azure Government cloud region.
- You can create a global peering of virtual networks in any Azure public cloud region, or in any China cloud region.
- Global peering of virtual networks in different Azure Government cloud regions isn't permitted.
- After you create a peering between virtual networks, the individual virtual networks are still managed as separate resources.
- Virtual networks can be peered across subscriptions and tenants.

## Things to consider when using peering
| Benefit                         | Description                                                                                                                                                                                                                                                                                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Private network connections** | When you implement Azure Virtual Network peering, network traffic between peered virtual networks is private. Traffic between the virtual networks is kept on the Microsoft Azure backbone network. No public internet, gateways, or encryption is required in the communication between the virtual networks. |
| **Strong performance**          | Because Azure Virtual Network peering utilizes the Azure infrastructure, you gain a low-latency, high-bandwidth connection between resources in different virtual networks.                                                                                                                                    |
| **Simplified communication**    | Azure Virtual Network peering lets resources in one virtual network communicate with resources in a different virtual network, after the virtual networks are peered.                                                                                                                                          |
| **Seamless data transfer**      | You can create an Azure Virtual Network peering configuration to transfer data across Azure subscriptions, deployment models, and across Azure regions.                                                                                                                                                        |
| **No resource disruptions**     | Azure Virtual Network peering doesn't require downtime for resources in either virtual network when creating the peering, or after the peering is created.                                                                                                                                                     |

# Gateway Transit and Connectivity
When virtual networks are peered, you can configure Azure VPN Gateway in the peered virtual network as a _transit point_. In this scenario, a peered virtual network uses the remote VPN gateway to gain access to other resources.

## Things to know about Azure VPN Gateway
Let's take a closer look at how Azure VPN Gateway is implemented with Azure Virtual Network peering.
- A virtual network can have only one VPN gateway.
- Gateway transit is supported for both regional and global virtual network peering.
- When you allow VPN gateway transit, the virtual network can communicate to resources outside the peering. In our sample illustration, the gateway subnet gateway within the hub virtual network can complete tasks such as:
    - Use a site-to-site VPN to connect to an on-premises network.
    - Use a vnet-to-vnet connection to another virtual network.
    - Use a point-to-site VPN to connect to a client.
- Gateway transit allows peered virtual networks to share the gateway and get access to external resources. With this implementation, you don't need to deploy a VPN gateway in the peered virtual network.
- You can apply network security groups in a virtual network to block or allow access to other virtual networks or subnets. When you configure virtual network peering, you can choose to open or close the network security group rules between the virtual networks.