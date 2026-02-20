AD DS is comprised of both logical and physical components:
**Logical Components**
- Partitions: Portion of the AD DS database
- Schema: Set of definitions of the object types and attributes that you use to define created objects
- Domains: Logical administrative container for objects such as users and computers
- Domain trees: Hierarchical collection of domains that share a common root domain and a contiguous DNS namespace
- Forests: Collection of one or more domains that have a common AD DS root, schema and global catalog
- Sites: 
- OUs: Container object for users, groups and computers
- Containers: Object that provides an organization framework for use in AD DS

**Physical Components**
- Domain controllers
- Data stores
- Global catalog servers
- RODCs

## AD DS Forest
A Forest is a top-level container in AD DS
- A unique implementation of AD DS that has a 1:1 relationship with its schema
- Made up of 1 or more trees
- Trust relationships

## AD DS Domain
Logical containers for managing user, computers, group and other objects
Described as:
- Replication boundary
- Administrative unit (Logical Grouping)

Provides:
- Authentication
- Authorization

# Comparing Service Accounts
![](/Images/compare_service_accounts.png)

# AD DS Management tools
![](/Images/ad_ds_management_tools.png)
# Manage AD DS domain controllers and FSMO roles
Domain controllers are servers that host the AD DS database (Ntds.dit) and SYSVOL

Host the Kerberos authentication service KDC services to perform authentication

Best practices:
- Use at least two domain controllers in a domain
- Use a RODC and Bitlocker

# Upgrade from a previous version of AD DS
(Look at documentation)
![](/Images/upgrade_from_previous_version_ad_ds.png)

# Domain and Forest Function Levels
- Determine the available AD DS capabilities within a domain or across a forest
- Control which Win Server OS can run on domain controllers in the domain or forest

Operating System Independence
- Function levels do not dictate the OS that can run on workstations and member servers within the domain or forest
- OS and function levels can be different

Backward Compatibility
- Functional levels can be raised to take advantage of new features. Rolling back requires using PowerShell or a forest recovery

# Manage the AD DS global catalog role
Global catalog - Partial read-only, searchable copy of all the objects in a forest

Configure the environment for the global catalog
- Single domain: Configure all the domain controllers to hold a copy of the global catalog
- Multiple-domain environment: Infrastructure master should not be a global catalog server unless all the DCs in the domain are also global catalog servers
- Multiple sites: Make at least one DC at each site a global catalog server

# Manage AD DS Operations Masters
In the multi-master replication model, some operations must be single master operations

Many terms are used for single master operations in AD DS, including:
Operations master (or operations master role)
Single mast role
FSMO: Flexible Single Master Operations roles are specialized tasks assigned to specific AD DCs to prevent conflicts in a multi-master replication environment

The 5 FSMOs:
**Forest operations master**
	- Schema Master: Handles updates to the AD scheme
	- Domain Naming Master: Controls the addition or removal of domains in the forest

**Domain operations master**
	- RID Master: Allocates Relative ID pools to domain controllers, ensuring unique Security Identifiers (SIDs) for new objects
	- PDC Emulator: Manages password update, accounts lockouts and acts as a time source for the domain
	- Infrastructure Master: Manages object references, such as renaming or moving objects between domains

# Schema
- Component that defines the rules and syntax of the AD DS database
- AD DS uses objects as units of storage
- Relationships among objects, rules, attributes and classes
You can manually add settings into the schema.

# Group Policy
Can set security settings and enforce custom settings on users/computers.
Scope:
- Sites
- Domains
- OUs

Processing Order:
1. Local GPOs
2. Site-linked GPOs
3. Domain-linked GPOs
4. OU-linked GPO
5. Child OU-linked GPOs

GPOs can be applied manually using `gpupdate /force` or automatically at:
- startup
- logon
- after 90min

**Block Inheritance**
Configure a domain or OU to prevent the inheritance of policy settings

**Enforce a GPO link**
- GPO takes the highest level of precedence
- Policy settings in that GPO prevail over any conflicting policy settings in other GPOs

**Evaluating Precedence**
Group policy inheritance tab displays the resulting precedence of GPOs

# Domain-based GPOs
Create and store domain-based GPOs on DCs and use to manage configuration centrally for domains user and computers

Two default GPOs
- Default Domain Policy
- Default Domain Controllers Policy

# Monitor and Troubleshoot AD DS
Tools:
- Task Manager
- Resource Monitor
- Event Viewer
- Performance Monitor



