# Implement Hybrid Identity
## Microsoft Entra ID Integration
### Select a Microsoft Entra ID integration model
Entra ID is part of the platform as a service (PaaS) offering and operates as a Microsoft-manged directory service in the cloud.
- Cloud-native and hybrid identity
- Users, Groups, devices management
- Open Cloud Standard Protocols
- Advanced security and Protocols
- Advanced security and protection of identity objects, tokens and logon sessions

**Microsoft Entra tenants**
- Multi-tenant
- Ensures isolation between individual directory instances

**Characteristics of Entra ID vs AD DS**
- No Kerberos -> Oauth & OpenID
- No LDAP -> Microsoft Graph, Rest API
- No Group Policy -> Conditional Access
- No Forest/Domain -> Federation
- No Virtual Machines -> Redundant PaaS

**Integration Options**
- Extending on-premises AD DS with Microsoft Entra ID
- Synchronizing AD DS with Microsoft Entra ID, by using password hash synchronization
- Implementing SSO between on-premises AD DS and Microsoft Entra ID
![](/Images/password_hash_sync.png)
![](/Images/pass_through_authentication.png)
![](/Images/federated_authentication.png)
### Plan for Microsoft Entra ID integration
- By using directory synchronization you can connect your on-premises AD DS with Entra ID
- Directory synchronization enables synchronization between on-premises AD DS and Entra ID for users, groups and contacts

**Microsoft Entra Connect**
A wizard-based tool designed to enable connectivity between an on-premises AD DS identity infrastructure and Azure.

Installing and configuring Entra Connect requires the following accounts:
- Azure account with Hybrid Identity Administrator permission in the Azure tenant
- On-premises account with Enterprise Administrator permissions in the on-premises AD DS
	**On-premises account must have:**
	- Enterprise Administrator permissions in AD DS
	- Local machine administrator permissions

**Microsoft Entra Connect Cloud Sync** provides similar capabilities to Entra Connect but is based on a provisioning agent, instead of the Entra Connect application.

Benefits of using Cloud Sync:
- Lightweight
- Manged from Entra ID
- Data stored in Entra ID
- Helps sync Entra ID to AD DS
## Directory  Synchronization with Microsoft Entra Connect
**Pre-deployment checks:**
1. Analyzing on-prem environment for invalid characters in AD DS object attributes and incorrect UPNs
2. Perform domain email discovery and user counts
3. Performing domain email discovery and user counts
4. Identifying domain-function levels and schema extensions and identifying custom attributes in use
5. Identifying proxy servers used for Microsoft Exchange or Skype for Business
6. Identifying Microsoft SharePoint domains
7. Evaluating client for SSO readiness
8. Recording network port use and DNS records related to Microsoft 365

**Active Directory health-check tools**
- IdFix Tools - Object synchronization errors
- ADModify.NET tool - Changes to multiple objects or bulk edits using powershell

### Install and Configure Directory Synchronization with Entra Connect
Requires a domain-joined computer to host the synchronization service.

**Requirements:**
1. Add your AD DS domain into Azure, verify the domain, and then set the domain as the primary domain
2. Download and install Microsoft Entra Connect
3. Run the Microsoft Entra Connect Configuration Wizard
	- **Express**
		- Single AD DS Forest
		- Built-in database
		- Recommended for most scenarios
	- **Advanced**
		- Multiple AD DS Forests
		- Microsoft SQL database
		- Used for more complex scenarios
4. Enable optional features such as password hash sync, password writeback and exchange hybrid deployment
5. Run Microsoft Entra Connect and let it configure the environment for directory synchronization
6. Validate the synchronization results
## Implement Seamless Sign-on (SSO)
Technology that works with AD FS (Federation Services) or with pass-through authentication

**Supported scenarios for pass-through authentication**
Microsoft Entra pass-through authentication helps ensure that services which rely on Microsoft Entra ID always validate passwords against an on-premises AD DS instance.

**How pass-through authentication works**
- Uses a component called Authentication Agent to authenticate users
- Microsoft Entra Connect installs the Authentication Agent during configuration
- After installation the Authentication Agent registers itself in your Microsoft 365 tenants Microsoft Entra ID
## Microsoft Entra Domain Services
Provides domain services such as Group Policy management, domain joining and kerberos authentication to your Microsoft Entra tenant.
These services are fully compatible with on-premises AD DS.

**Scenarios that utilize Domain Services**
- Secure administration of Azure VMs
- On-premises applications that use LDAP bind authentication
- On-premises applications that use LDAP read to access the directory
- On-premises services or daemon application
- Remote desktop services in Azure
**Considerations**
- Domain Services-managed domains use a single, flat OU structure by default
- Domain Services uses a built-in GPO each for the users and computers containers
- Domain Services support the base Active Directory computer object schema
- You cant change passwords directly in a Domain Services-managed domain
### Implement Domain Services
To implement, configure and use Domain Services you must:
- Have a Microsoft Entra Tenant created on a Entra ID subscription
- Have password hash synchronization deployed with Microsoft Entra Connect
- Select the DNS domain name that you will use for this service
- Select the domain that you will synchronize with your on-premises environment

You must select a VNet to which you will connect this service.
(Because Domain Services provides functionalities for on-premises resources you must have a VNet between your local and Azure environments).

During provisioning Domain Services create two enterprise applications in your Microsoft Entra tenant:
- Domain Controller Services
- AzureActiveDirectoryDomainControllerServices
## Mange Windows Server in a Microsoft Entra Domain Services environment
**Administrators can perform:**
- Configure the built-in GPO for the containers AADDC Computers and AADDC Users, in the managed domain​
- Administer DNS on the managed domain​
- Create and administer custom OUs on the managed domain​
- Gain administrative access to computers joined to the managed domain

**Cannot perform:**
- Extend the schema of the managed domain​
- Connect to domain controllers for the managed domain using Remote Desktop​
- Add domain controllers to the managed domain​
- Employ Domain Administrator or Enterprise Administrator privileges for the managed domain

**Enable user accounts for Domain Services**
- To authenticate users on the managed domain, Domain Services needs password hashes in a format that’s suitable for NTLM and Kerberos authentication.​
- Once appropriately configured, the usable password hashes are stored in the Microsoft Entra Domain Services managed domain.​
- Synchronized credential information in Microsoft Entra ID can’t be re-used if you later create a Domain Services–managed domain.​
- The steps to generate and store these password hashes are different for cloud-only user accounts created in Microsoft Entra ID versus user accounts that are synchronized from your​  on-premises directory using Microsoft Entra Connect.​
- For cloud-only user accounts, users must change their passwords before they can use Domain Services.​