# Azure Role-Based Access Control
When identity and access most organizations that are considering using the public cloud are concerned about two things;
1. Ensuring that when people leave the organization, they lose access to resources in the cloud.
2. Striking the right balance between autonomy and central governance. For example, giving project teams the ability to create and manage virtual machines in the cloud, while centrally controlling the networks those VMs use to communicate with other resources.

# Azure RBAC
An authorization system build on Azure Resource Manager that provides fine-grained access management for resources in Azure. You can grant exact access that users need to do their jobs.

You can grant access by assigning the appropriate Azure role to users, groups and applications at a certain scope. The following diagram depicts how the subscription administrator roles, Azure roles and Entra roles are related at a high level. Child scopes, such as service instances, inherit roles assigned at a higher scope, like an entire subscription.
![](/Images/assigned_roles.png)

# What can be done with RBAC
Some example scenarios you can implement:
- Allow one user to manage virtual machines in a subscription and another user to manage virtual networks.
- Allow a database administrator group to manage SQL databases in a subscription.
- Allow a user to manage all resources in a resource group, such as virtual machines, websites, and subnets.
- Allow an application to access all resources in a resource group.

# How does RBAC work
### 1. Security principal (who)

A _security principal_ is just a fancy name for a user, group, or application to which you want to grant access.

![An illustration showing security principal including user, group, and service principal.](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/media/2-rbac-security-principal.png)

### 2. Role definition (what)

A _role definition_ is a collection of permissions. It's sometimes just called a role. A role definition lists the permissions the role can perform such as read, write, and delete. Roles can be high-level, like Owner, or specific, like Virtual Machine Contributor.

![An illustration listing different built-in and custom roles with zoom-in on the definition for the contributor role.](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/media/2-rbac-role-definition.png)

Azure includes several built-in roles that you can use. The following lists four fundamental built-in roles:

- **Owner**: Has full access to all resources, including the right to delegate access to others.
- **Contributor**: Can create and manage all types of Azure resources, but can’t grant access to others.
- **Reader**: Can view existing Azure resources.
- **User Access Administrator**: Lets you manage user access to Azure resources.

If the built-in roles don't meet the specific needs of your organization, you can create your own custom roles.

### 3. Scope (where)

_Scope_ is the level where the access applies. This is helpful if you want to make someone a Website Contributor but only for one resource group.

In Azure, you can specify a scope at multiple levels: management group, subscription, resource group, or resource. Scopes are structured in a parent-child relationship. When you grant access at a parent scope, the child scopes automatically inherit those permissions. For example, if a group is assigned the Contributor role at the subscription scope, it will inherit the role for all resource groups and resources within the subscription.

![An illustration showing a hierarchical representation of different Azure levels to apply scope. The hierarchy, starting with the highest level, is in this order: Management group, subscription, resource group, and resource.](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/media/2-rbac-scope.png)