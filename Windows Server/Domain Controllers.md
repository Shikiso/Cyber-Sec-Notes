## Active Directory Domain Service
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

## AD DS Schema
AD DS schema is the blueprint for an [Active Directory](https://www.google.com/search?client=firefox-b-d&q=Active+Directory&mstk=AUtExfAtC28rGurD00iyZBXy__U6A3-BSPyeYGtrkP2Z5-WI6E5uyftgV7NOjRGiJkX-fAHAbgkj0EXuSVXea3sSipGq4KEBa-20x45RY8tSZn-lUcQdzyJ940IiU5Yt4NRYTokg00k2t2QehLu229ygsm_Tz7Akj5vq6mYVdBiKC2sntU5jugdsynfKXo85FcD_JLbWliDudkGC59gxNSlpeTxhaEgB5rQ-48ApYPH6nQ_byvvmDBPVndU22JTeVFA4Kxha3OSsKozrZW9sk6S1eNRbdCWFWz133wjp12vct9T52Q&csui=3&ved=2ahUKEwiso6DH6_OPAxX0k1YBHTLDGsUQgK4QegQIARAE) forest, containing formal definitions for all object classes (e.g., users, computers) and their associated attributes (e.g., name, email) that can exist within the directory. The attributes are added and remove automatically.

## AD DS Forest
A forest is multiple domain servers grouped together.
![[Pasted image 20250925195248.png]]

## AD DS Domain
AD DS requires one or more domain controllers.
All domain controllers hold a copy of the domain database, which is continually synchronized.
The domain is the context within which user accounts, computer accounts and groups are created.
The domain is an administrative center for configuring and managing objects.

## Organizational Units
OUs are containers to group objects within a domain.
- You cannot apply GPOs to containers
- Containers are used for system objects and as the default location for new objects
Create OUs to:
- Configure objects by assigning GPOs to them
- Delegate administrative permissions

## Azure AD
A cloud-based identity and access management (IAM) solution that helps organizations manage user access to applications and data in the cloud and on-premises environments.
![[Pasted image 20250925200238.png]]

## Domain Controller
Servers that host the AD DS database (Ntds.dit) and SYSVOL

Host the Kerberos authentication service and KDC services to perform authentication.

Best practice:
- Use at least 2 domain controllers in a domain
- Use an RODC or BitLocker

## Global catalog
Hosts a partial attribute set for other domains in the forest.
Supports queries for objects throughout the forest.

## Domain Controller SRV records
Clients find domain controllers through DNS lookup.
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
![[Pasted image 20250925202846.png]]