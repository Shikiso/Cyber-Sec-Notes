(Will fix later)
Install AD DS server role
Install-WindowsFeature –Name AD-Domain-Services –ComputerName SEA-SVR1

Verify AD DS role is installed
Get-WindowsFeature –ComputerName SEA-SVR1

Run command on different server
(make sure server is added in all servers has ad ds)

Invoke-Command -ComputerName SEA-SVR1