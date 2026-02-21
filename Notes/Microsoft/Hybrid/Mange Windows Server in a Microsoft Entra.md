# Domain Services environment
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