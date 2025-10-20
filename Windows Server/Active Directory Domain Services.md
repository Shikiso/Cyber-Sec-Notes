AD DS forms the foundation in which networks that run Windows operating systems rely on. The AD DS database stores domain objects, such as user accounts, computing accounts and groups. AD DS provides a searchable, hierarchical directory and method for applying configuration and security settings for objects in the enterprise.

## AD DS Components
AD DS is comprised of both logical and physical components:

| Logical      | Physical               |
| ------------ | ---------------------- |
| Partitions   | Domain controllers     |
| Schema       | Data stores            |
| Domains      | Global catalog Servers |
| Domain trees | RODCs                  |
| Forests      |                        |
| Sites        |                        |
| OUs          |                        |
| Containers   |                        |
You can use AD DS options to perform actions such as :
- Installing, configuring and updating applications
- Managing the security infrastructure
- Enabling Remote Access Service and Direct Access
- Issuing and managing digital certificates
This most used feature is Group Policy, which allows you to configure centralized policies for managing most objects in AD DS.

### Description of Components
| Logical component | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Partition         | A partition, or naming context, is a portion of the AD DS database. Although the database is one file named Ndts.dit, different partitions contain different data. For example, the schema partition contains a copy of the Active Directory schema. The configuration partition contains the configuration objects for the forest, and the domain partition contains the users, computers, groups, and other objects specific to the domain. Copies of a partition can be stored on multiple domain controllers and updated through directory replication. |
| Schema            | A schema is the set of definitions of the object types and attributes that you use to define the objects created in AD DS.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Domain            | A domain is a logical administrative container for objects such as users and computers. A domain maps to a specific partition and can be organized with parent-child relationships to other domains.                                                                                                                                                                                                                                                                                                                                                        |
| Domain tree       | A domain tree is a hierarchical collection of domains that share a common root domain and a contiguous Domain Name System (DNS) namespace.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Forest            | A forest is a collection of domains that share a common AD DS root and schema, which have a two-way trust relationship.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Site              | A site is a container for AD DS objects, such as computers and services that are specific to their physical location. This is in comparison to a domain, which represents the logical structure of objects, such as users and groups, in addition to computers.                                                                                                                                                                                                                                                                                             |
| Subnet            | A subnet is a portion of the network IP addresses of an organization assigned to computers in a site. A site can have more than one subnet.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| OU                | An OU is a container object for users, groups, and computers that provides a framework for delegating administrative rights and administration by linking Group Policy Objects (GPOs).                                                                                                                                                                                                                                                                                                                                                                      |
| Container         | A container is an object that provides an organizational framework for use in AD DS. Some containers are created by default, or you can create custom containers. Containers cannot have GPOs linked to them.                                                                                                                                                                                                                                                                                                                                               |

| Physical component                 | Description                                                                                                                                                                                                                                                                                     |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain controller                  | A domain controller contains a copy of the AD DS database. For most operations, each domain controller can process changes and replicate the changes to all the other domain controllers in the domain.                                                                                         |
| Data store                         | A copy of the data store exists on each domain controller. The AD DS database uses Microsoft Jet database technology and stores the directory information in the Ntds.dit file and associated log files. The C:\Windows\NTDS folder stores these files by default.                              |
| Global catalog server              | A global catalog server is a domain controller that hosts the global catalog, which is a partial, readonly copy of all the objects in a multiple-domain forest. A global catalog speeds up searches for objects that might be stored on domain controllers in a different domain in the forest. |
| Read-only domain controller (RODC) | An RODC is a special, readonly installation of AD DS. RODCs are common in branch offices where physical security is not optimal, IT support is less advanced than in the main corporate centers, or line-of-business applications need to run on a domain controller.                           |

## AD DS Schema
AD DS schema is the component that defines all object classes and attributes that AD DS uses to store data. All domains in a forest contain a copy of the schema that applies to that forest. Any changes to the schema replicates to every domain controller in the forest from the schema master, (usually the first domain controller in the forest).

AD DS uses objects as units of storage. The schema defines all object types. Each time the directory handles data, the directory creates the object and stores the data.
Object definition specify both the types of data that the objects can store and the syntax of the data. You can only create objects that the schema defines.

In AD DS the schema defines:
- Objects that store data in the directory
- Rules that define the structure of the objects
- The structure and content of the directory itself

AD DS schema objects consist of attributes which are group together in classes. Each class has rules which define attributes are mandatory and which are optional.

Only users in the Schema Admins group can modify the AD DS schema but you cannot remove anything. You can only extend it by using extensions or by modifying attributes of existing objects.
## AD DS Forest
![](/Images/forest.png)
A forest is a top-level container in AD DS. Each forest is a collection of domain trees that share a common directory schema and a global catalog. A domain tree is a collection of one or more domains that share a continuous namespace.

The first domain created in a forest is called the **forest root domain**. Which contains a few objects that do not exist in other objects. These being:
 - **The schema master role**. This is a special, forest-wide domain controller role. Only one schema master exists in any forest. You can change the schema only on the domain controller that holds the schema master. 

- **The domain naming master role**. This is also a special, forest-wide domain controller role. Only one domain naming master exists in any forest. Only the domain naming master can add new domain names to the directory. 

-  **The Enterprise Admins group**. By default, the Enterprise Admins group has the Administrator account for the forest root domain as a member. The Enterprise Admins group is a member of the local Administrators group in every domain in the forest. This allows members of the Enterprise Admins group to have full control administrative rights to every domain throughout the forest. 

- **The Schema Admins group**. By default, the Schema Admins group has no members. Only members of the Enterprise Admins group or the Domain Admins group (in the forest root domain), can add members to the Schema Admins group. Only members of the Schema Admins group can make changes to the schema.
## AD DS Domain
An AD DS domain is a logical container for managing user, computer, group and other objects. The AD DS database stores all domain objects and each domain controller stores a copy of the databse.
AD DS database common objects:
- User accounts
- Computer Accounts
- Groups

### Replication
When you make changes to any object in the domain, the domain controller replicates that change to all other domain controllers within the domain. If multiple domains exist in the forest only subsets of the changes replicate to other domain.

## Organizational Units
OUs are containers to group objects within a domain that you can use to consolidate users, computers, groups and other objects.
- You cannot apply GPOs to containers
- Containers are used for system objects and as the default location for new objects
Create OUs to:
- Configure objects by assigning GPOs to them
- Delegate administrative permissions

## Domain Controller
A domain controller is a server that stores copies of the AD DS database (Ntds.dit) and the SYSVOL folder. All domain controllers except RODCs store ad read/write copy of bothj Ntds.dit and the SYSVOL folder.

A domain controller is responsible for authenticating user and computer credentials, determining what authorization users have, keeping AD databases in sync, enforcing group policy and often hosting DNS for the domain.

Host the Kerberos authentication service and KDC services to perform authentication.

Best practice:
- Use at least 2 domain controllers in a domain
- Use an RODC or BitLocker for security reasons

## Global catalog
A Global Catalog is a read-only, searchable copy of all objects in an AD forest. Containing only a subnet of each objects attributes. It allows fast searches for objects across different domains in a forest, since regular DCs can only search within their domain.
By default the first DC in the forest root domain is the only global catalog server, but additional ones can be configured.

The global catalog is essential for:
- **Cross-domain lookups** (e.g., finding a user in another domain)
- **Exchange Server email routing**
- **User logins**, where the DC checks **universal group memberships**
        
Some best practices are:
- In a **single-domain** setup, make **all domain controllers** GC servers.
- In **multi-domain** environments:
- The **infrastructure master** should **not** be a GC unless all DCs are.
- Place at least one **GC server per site** to reduce inter-site traffic.
 - Many organizations choose to make **every DC a GC** for simplicity.

## Domain Controller SRV records
When users sign in to AD DS their computers look in DNS for SRV records to locate the nearest domain controller. SRV records contain information about available services.
Domain controllers dynamically register their addresses with DNS.

The result of DNS queries for domain controllers are returned in this order:
1. A list of domain controllers in the same site as the client
2. A list of domain controllers in the nest closest site, if none are available in the same site
3. A random list of domain controllers in other sites, if no domain controller is available in the nest closest site.

## AD DS sign-in process
1. User account is authenticated to the DC
2. DC returns a TGT
3. Client uses TGT to apply for workstation access
4. DC grants access
5. Client uses TGT to apply for server access
6. DC returns access
![](/Images/AD_DS_sign_in.png)