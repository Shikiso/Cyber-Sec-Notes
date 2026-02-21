# Concept of Least Privilege
Least privilege is the concept of restricting access rights and permissions to only those rights permissions needed to perform a specific task or job role.

# Security Principals

| Group             | Description                                               |
| ----------------- | --------------------------------------------------------- |
| Enterprise admins | Can perform forest-wide administrative changes in AD      |
| Domain admins     | Have administrative rights on all domain-joined computers |
| Schema admins     | Can modify the properties of the AD DS schema             |
| Administrators    | Local security group, affecting local machines            |

# Modify Group Memberships
Use the Restricted Group feature:
- Open Group Policy Management and then create and link a GPO to the domain object
- Open the GPO for editing
- Locate Computer Configuration, Policies, Windows Settings, Security Settings, Restricted Groups
- Right-click or active the context menu for Restricted Groups and select Add Group
- In the Add Group dialog box add the required group
- Add the members to the group or add the group to another group as a member

# Determine Currently Assigned Rights
**How to use the Local Security Policy console to determine what rights are assigned**
1. Select Start and then select Windows Administrative Tools
2. Select Loyal Security Policy
3. In Local Security Policy expand Local Policies and the expand User Rights Assignment
4. Review and if necessary edit the Security Setting value for each Policy listed

# Implement User Account Control
**How to control UAC prompts and behavior by using GPOS:**
1. Open Linked GPO: Computer Configuration > Policies Windows Settings > Security Settings > Local Policies, Security Options
2. Open User Account Control: Behavior of the elevation prompt for administrators setting, select Define this policy setting and select the required setting
3. Open User Account Control: Behavior of the elevation prompt for standard users setting, select Define the Policy setting and then select the required setting

# Implement Delegated Privileges
**Use the Delegation of Control Wizard to limit administrative access*
- You can delegate more granular privileges to users/groups
- You can combine permissions to create and assign custom tasks

# Privileged Access Workstation (PAW)
A computer that you can use for performing tasks such as the administration of:
- Identity systems
- Cloud services
- Other sensitive services
Never use PAW for web browsing, email and other common apps
Microsoft recommends using Win 11 Enterprise

## PAW hardware profiles
**Dedicated hardware**
Separate dedicated devices for user tasks versus administrative tasks

**Simultaneous use**
A single device that can run user tasks and administrative tasks concurrently by running two operating systems

# Jump Servers
- A hardened server used to access and manage devices in different security zones
- Known as bastion hosts
- Do not have sensitive data (usually)
- Can help enhance security for medium-sized organizations

## Considerations for implementing jump servers
- Setup remote desktop gateway for implement required restrictions
- Install Hyper-V to build VM for each admin
- Enable Server features: UEFI secure boot, Virtualization support, Signed Kernel mode drivers
- Install Remote administration tools
- Required RDP connectivity to Admins VMs













