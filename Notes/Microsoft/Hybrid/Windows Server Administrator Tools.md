# Windows Admin Center (WAC)
- Gateway to manage servers through powershell remoting and WMI
- Web server with UI to management station
- Easy to use
- Manage from internet

# Server Manager
- Configure local server
- Add roles and features
- Create server group
- Add other servers to manage

# Remote server Administration Tools

| Tool                                        | Description                                                                                                                                 |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Active Directory Certificate Services Tools | Includes Certificate Authority, Certificate Templates, Enterprise PKI and Online Responder Management snap-ins                              |
| DHCP Server Tools                           | Includes DHCP management console, the DHCP Server cmdlet module for Windows Powershell and the Netsh command-line tool                      |
| DNS Server Tools                            | Includes DNS Manager snap-in, DNS module for Windows Powershell and Ddnscmd.exe command-line tool                                           |
| Shielded VM Tools                           | Includes Provisioning Data FIle Wizard and Template Disk Wizard                                                                             |
| IP Address Management (IPAM) Tools          | Includes tools for managing remote IPAM server                                                                                              |
| Remote Access Management Tools              | Includes graphical and Powershell tools for managing the Remote Access role                                                                 |
| Network Load Balancing Tools                | Includes Network Load Balancing Manager, Network Load Balancing Windows PowerShell cmdlets, and the NLB.exe and WLBS.exe command-line tools |
| Windows Server Update Services Tools        | Includes Windows Server Update Services snap-in, WSUS.msc and PowerShell cmdles                                                             |

# Post Installation Configuration of Windows Server
**What must you configure?**
1. Computer name
2. Workgroup (not important)
3. Network settings
4. Time Zone
5. Locale and language settings
6. Roles and features
7. Firewall settings
8. Activation

## Tools
- Server Manager: Local server settings
- WAC - Post-installation configuration
- Answer files: Automating installation process
- ConfigMgr: Used for post-installation tasks for windows server

# Just Enough Administration
Provides Windows OS with RBAC functionality built on PowerShell remoting.
An authorized user connects to a specially configured endpoint and uses a specific set of Windows Powershell cmdlets, parameters and parameter values

Only work with powershell
Only works for windows server 2016+ and Windows 10+