# CMD
## Utility Tools
`MSConfig` - Troubleshoot startup issues
`compmgmt.msc` Computer Management:
- `Task Scheduler` - Manage common tasks with automation
- `Disk Management` - Perform advanced storage tasks
- `Services & Applications` - Allows scripts to manage device
`msinfo32` - Gathers information about your computer
`resmon` - Displays per-process and aggregate CPU, memory, disk and network information
`cmd` - Command line to interact with OS
`regedt32` - Windows Registry editor

## BitLocker
BitLocker Drive Encryption is a data protection feature that ingrates with the OS and addresses the threats of data theft or exposure from lost, stolen or inappropriately decommissioned computers.

## Volume Shadow Copy Service
The VSS coordinates the required actions to create a consistent shadow copy of the data that is to be backed up.

If VSS is enabled on a system:
- Create a restore point
- Perform system restore
- Configure restore settings
- Delete restore points
## System Information
`set` - Shows your paths
`ver` - Gets OS version
`systeminfo` - Displays system information
`dir` - Show files and directory in working directory
	`/a` - Shows hidden files
	`/s` - Displays files in current and sub directories
`tree` - visually show directories (sub and current)
`type` - Display file contents
`tasklist` - Show running tasks
	`/FI "imagename eq <process>"` - To find process with name
`taskkill` - Kill a task
`chdsk` - Checks file system for errors
`driverquery` - Displays list of install drivers
`sfc /scannow` - Scans system files for corruption and tries to repair them

## Network
`ipconfig` - Shows network information. Add /all to get info about config
`ping` - Pings target
`tracert` - Trace Route of network route
`nslookup` - Lookup host/domain and return IP address
`netstat` - Displays current network connections
- `-a` displays all established connections and listening ports
- `-b` shows the program associated with each listening port and established connection
- `-o` reveals the process ID (PID) associated with the connection
- `-n` uses a numerical form for addresses and port numbers
## Quality Of Life
`more` - Same as less in linux

# Powershell
## Basics
- `Get-Command` - List all commands
- `Get-Content` - Gets content of file
- `Set-Location` - Changes working directory
- `Get-Help <cmd>` - Get manual to command
- `Get-Alias` - Lists all aliases available
- `Find-Module -Name "name"` - Search for modules
- `Install-Module -Name "name"` - Install a module

## File System
- `Get-ChildItem` -list directory contents
- `Set-Location` - navigate directories
- `New-Item` - create a file or directory
- `Remove-Item` - delete file/directory
- `Get-Content` - read file content

## Sorting Data
- `Sort-Object` - sorts objects by property
- `Where-Object` - filter objects based on conditions
- `Select-Object` - select properties from objects

- `-ne`- not equal
- `-gt` - greater than
- `-ge` - greater than or equal to
- `-lt` - less than
- `-le` - less than or equal to

## System and Network Information
- `Get-ComputerInfo` - Get system information
- `Get-NetIPConfiguration` - Shows network interface details
- `Get-LocalUser` - Lists local user accounts

## System Analysis
- `Get-Process` - List running processes
- `Get-Service` - Show services and their statuses
- `Get-NetTCPConnection` - Displays active TCP connections
- `Get-NetUDPEndpoint` - List active UDP endpoints

## Scripting
`Invoke-Command` - Used for executing commands on remote systems