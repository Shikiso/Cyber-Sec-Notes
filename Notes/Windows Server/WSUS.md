# (Windows Server Update Service)
WSUS is Windows Server Update Services

### Server Deployment Options
WSUS Implementation:
	- Single server
	- Mutliple servers
	- Disconnected servers
WSUS hierachies:
	- Antonomous mode
	- Replica mode
WSUS database:
	- Windows Internal Database
	- SQL Server database

### Update management process
<IMG>

### Server requirements
Software requirements:
	IIS
	Microsoft .NET Framework 4.6 or newer
	Microsoft Report Viewer Redistributable 2008 or newer
	SQL Server 2012 SP1, SQL Server 2012, SQL Server 2008 R2 SP2, SQL Server 200 R2 SP1, or WID
Hardware requirements:
	1.4 GHz or faster x64 processor
	2GB of RAM or greater
	10GB available disk space (40GB+ is recommended)

### Configuring clients
Use a GPO to configure automatic updates and specify intranet Microsoft Update server location

For windows 8 and windows server 2012 you can use Automatic Maintenance to control the update process

For older OS:
	Automatically download updates
	Automatically install updates

Windows 10+ you can defer updates for up to one month

### Update management process
WSUS administration
	- Manage updates
	- Configure computer groups
	- View computer status
	- View synchronization informaiton
	- Config & view WSUS reports
	- Config WSUS settings and options

Computer groups
	- Can be used to organize WSUS clients

Approving updates
	- Can be done automatically...dont do this
	- Declined if not needed
	- Removed if causes problems
	- Test updates before approval

Configuring atutomatic updates
	- Config clients to use WSUS as source for updates
	- Can use Group Policy to config clients

Deplying updates by using WSUS
WSUS reporting
	- Update reports
	- Computer updates
	- Synchronization updates

WSUS troubleshooting
Clients not appearing in WUS:	Check GPO and client settings
when WSUS server stops:		Check db server, reinstall WSUS
Cannot connect to WSUS:		Check net connectivity, telent to http/s ports
Other problems:			                Server/client diagnostics tool
