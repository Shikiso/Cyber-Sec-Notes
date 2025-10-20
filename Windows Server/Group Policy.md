Group policy is a framework in Windows OS with components that reside in AD DS on domain controllers, and on each Windows server and client. With these components you can manage configuration in an AD DS domain.

# Managing Group Policy
Group policy allows centralized management of thousands of system and user configurations across a network.
 Types of policy settings (these settings refresh at logon/startup + every 90-120min):
- User Configuration
- Computing Configuration

## Configuration settings:
### 1. **Software Settings**
- Used to deploy, maintain, or remove software applications through GPOs.
### 2. **Windows Settings**
- Includes **Scripts**, **Security Settings**, and **Policy-Based QoS**.
#### a. **Scripts Node**
- Lets you assign:
    - **Startup/shutdown scripts** (Computer Configuration)
    - **Logon/logoff scripts** (User Configuration)
- Scripts can be written in VBScript, JScript, PowerShell, batch files, etc.
- You can control the **order** and **timeout** of script execution.
#### b. **Security Settings Node**
- Used by admins to configure security options via GPOs instead of security templates.
#### c. **Policy-Based QoS Node**
- Manages **network traffic priority** (e.g., giving Finance applications more bandwidth during reporting periods).
#### d. **Folder Redirection (User Configuration only)**
- Redirects user folders (Documents, Desktop, etc.) to a **network location** for centralized storage and management.

## Administrative Templates
Administrative templates contain registry-based policy settings which are used to configure most Windows and software behaviors.

# Group Policy Objects
You define policy settings within a GPO. A GPO is an object that contains one or more policy settings that apply to one or more configuration settings for a user or a computer.

(You manage GPOs using the GPMC)
The GPMC displays GPOs in a container named Group Policy Objects. To create a new GPO in a domain, right-click the Group Policy Objects container, click New, and then specify a name for the GPO. To modify the configuration settings in a GPO, right-click the GPO, and then click Edit. This opens the Group Policy Management Editor window. To create a GPO in Windows PowerShell, you run the following cmdlet: 

`New-GPO -Name “Sales GPO” -comment "This is the sales GPO"`

It is also possible to create a GPO and link it to the domain or an OU when it is created, by right-clicking the container, and then clicking Create a GPO in the domain and link it here.

# Group Policy Object Inheritance
You can create and link GPOs to a site, domain or OU. When you apply multiple GPOs to the same container this aggregates the settings in the GPOs. For most policy settings the GPO with the highest precedence and that contains the specific setting determines the settings final value.
GPOs are processed on a client computer in the following order:
1. Local GPOs
2. Site-level GPOs
3. Domain-level GPOs
4. OU GPOs, including nested OUs