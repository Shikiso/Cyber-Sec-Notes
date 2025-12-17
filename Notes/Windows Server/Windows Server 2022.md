## Windows server editions
Essentials - for small businesses (not really used)
Standard - Full functionality, only support 2 vms
Data center - Full functionality, unlimited vm usages

## Min hardware req
Process architecture x64
Processor speed 1.4Ghz
RAM 512MB
Hard drive space 32GB
## Window server versions
Desktop - full server installation
Server Core - minimum installed (default, no gui)

## Manage servers remotely
- Remote Server Administration Tools (RSAT)
- Windows Powershell remoting
- Powershell direct
-  Remote shell
- Remote Desktop
- Group Policy

## Servicing channels
LTSC:
- New major version every 2-3 years 
- Tradition deployment and versioning
- Available in Server Core or Server with Desktop
Annual channel :
- New version every 12 months
- Only available through a Microsoft Software Assurance agreement

## Post installation check list
- config IP
- Set name
- Join active dir domain
- config time zone
- enable automatic updates
- add roles and features
- enable remote desktop
- config firewall
- can use sconfig.cmd in core edition

## Upgrade
can only upgrade 2 versions
needs to be same edition
and requires same processor architecture

## Migration
Does not affect current infrastructure
perform software product migration in separate environment
Perform migration of server roles, features and settings in separate environment

## Solution accelerators tools
MDT
MAP
Windows Server Migration tools

## Licensing
Manual - good for small number of servers
Automatic - good for large amount of servers

## AD DS Components
Locgical:
		- Partitions
		- Schema
		- Domains
		- Domain trees
		- Forests
		- Sites
		- OUs
		- Containers
Physical:	
		- Domain controllers
		- Data stores
 		- Global catalog servers
		- RODCs

## Definitions
Organizational Units (OUs) - Containers to group object within a domain
Active Directory (AD) - Organizes and manages network resources like users, computers and applications
Domain Controllers - Servers that host the AD DS database
Domain Service Databse - Ntds.dit
Group Policy Object (GPO) - Collection of settings used in AD to manage security and user configs
