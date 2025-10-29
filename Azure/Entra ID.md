Entra ID is a cloud-based identity and access management service.
Entra ID is used for managing identities, enforcing access policies and securing you applications and data in the cloud and on-premises.

Entra works as a Microsoft-managed directory service in the cloud.
Entra ID provides better security when accessing cloud-based resources this is done by providing theses resources:
- Configuring access to applications
- Configuring single sign-on (SSO) to cloud-based SaaS applications
- Managing users and groups
- Provisioning users
- Enabling federation between organizations
- Providing an identity management solution
- Identifying irregular sign-in activity
- Configuring multi-factor authentication
- Extending existing on-premises Active Directory implementations to Microsoft Entra ID
- Configuring Application Proxy for cloud and local applications
- Configuring Conditional Access for users and devices

# Entra Tenants
Entra ID is multi-tenant (application servers multiple tenants) and is implemented specifically to ensure isolation between its individual directory instances.

Each Entra tenant is assigned the default DNS domain name consisting of a unique prefix.

# Entra Schema
The Entra schema contains fewer object types than AD DS. (It does not include a definition of the computer class).

The lack of support for tradition computer domain membership means that you can't use Entra ID to manage computer or user settings by using traditional management techniques such as Group Policy Objects. Entra ID also does not include organizational units.

Entra ID is best at providing directory services; storing and publishing user, device and application data and handling authentication and authorization of users, devices and applications.

# The difference between Entra ID and AD DS
| Entra ID                                                                                                                                                                                                | AD DS                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Microsoft Entra ID is primarily an identity solution, and it’s designed for internet-based applications by using HTTP (port 80) and HTTPS (port 443) communications.                                    | AD DS is a true directory service, with a hierarchical X.500-based structure.                 |
| Microsoft Entra ID is a multi-tenant directory service.<br>                                                                                                                                             | AD DS is a true directory service, with a hierarchical X.500-based structure.                 |
| Microsoft Entra users and groups are created in a flat structure, and there are no OUs or GPOs.                                                                                                         | AD DS is a true directory service, with a hierarchical X.500-based structure.<br>             |
| You can't query Microsoft Entra ID by using LDAP; instead, Microsoft Entra ID uses the REST API over HTTP and HTTPS.                                                                                    | AD DS primarily uses the Kerberos protocol for authentication.                                |
| Microsoft Entra ID doesn't use Kerberos authentication; instead, it uses HTTP and HTTPS protocols such as SAML, WS-Federation, and OpenID Connect for authentication, and uses OAuth for authorization. | AD DS uses OUs and GPOs for management.                                                       |
| Microsoft Entra ID includes federation services, and many third-party services such as Facebook are federated with and trust Microsoft Entra ID.                                                        | AD DS includes computer objects, representing computers that join an Active Directory domain. |
|                                                                                                                                                                                                         | AD DS uses trusts between domains for delegated management.                                   |

# Entra ID as a Directory Service for Cloud Apps
When deploying cloud services you need to have directory services in the cloud to provide authentication and authorization for these services. Because of this each service that needs authentication will create its own Entra tenant.

# Domain Services
When switching from AD DS to Azure you need to implement a [site-to-site VPN](/Networking/VPN.md) between your local infrastructure and the Azure IaaS.

Because of this Entra Domain Services is provides as an alternative. This service provides domain services such as Group Policy management, domain joining and Kerbose authentication to Entra tenants.

Since Entra ID can integrate with your local AD DS when you implement Entra Connect, users can utilize organizational credentials in both on-premises AD DS and in Entra Domain Services.

Entra Domain Services provides benefits such as:
- Administrators don't need to manage, update, and monitor domain controllers.
- Administrators don't need to deploy and manage Active Directory replication.
- There’s no need to have Domain Admins or Enterprise Admins groups for domains that Microsoft Entra ID manages.

If implementing Entra Domain Services be aware of these limitations:
- Only the base computer Active Directory object is supported.
- It’s not possible to extend the schema for the Microsoft Entra Domain Services domain.
- The organizational unit (OU) structure is flat and nested OUs aren't currently supported.
- There’s a built-in Group Policy Object (GPO), and it exists for computer and user accounts.
- It’s not possible to target OUs with built-in GPOs. Additionally, you can't use Windows Management Instrumentation filters or security-group filtering.