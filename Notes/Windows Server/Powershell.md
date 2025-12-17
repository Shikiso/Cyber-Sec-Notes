## Active Directory
| Description          | Command                                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------------------- |
| Set User password    | `Set-ADAccountPassword <name> -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose` |
| Force password reset | `Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose`                                            |
## Group Policy
| Description                                                      | Command    |
| ---------------------------------------------------------------- | ---------- |
| Forces immediate Group Policy Refresh                            | `gpupdate` |
| Displays which GPO, and settings apply to a user or computer<br> | `gpresult` |
## Storage/Partition

| Description                                   | Command                                                                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Get available disks                           | `Get-Disk \| Where-Object PartitionStyle –Eq "RAW"`                                                                               |
| Initialize disk<br>                           | `Initialize-disk {number}`                                                                                                        |
| Review partition table                        | `Get-disk`                                                                                                                        |
| Create a ReFS volume with all available space | `New-Partition -DiskNumber {num} -UseMaximumSize -AssignDriveLetter \| Format-Volume -NewFileSystemLabel "NAME" -FileSystem ReFS` |
| Dismount Virtual hard disk                    | `Dismount-vhd {disk}`                                                                                                             |
| Check properties of vhd:                      | `Get-vhd {disk}`                                                                                                                  |
| Convert VHD to VHDX                           | `Convert-VHD -Path {disk} -DestinationPath {disk.vhdx}`                                                                           |
| Change sector size                            | `Set-VHD –Path {disk} –PhysicalSectorSizeBytes {size}`                                                                            |
| Optimize .vhdx file                           | `Optimize-VHD –Path {disk} –Mode Full`                                                                                            |
## DISKPART
| Description                    | Command                                                                                                                                                                           |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Create new disk using Diskpart | `1. Diskpart`<br>`2. List disk`<br>`3. Select disk {num}`<br>`4. Convert dynamic`<br>`5. Create volume NAME size={size} disk={num}`<br>`6. Assign letter={letter}`<br>`7. Format` |
| To Extend size                 | `Extend size {size}`                                                                                                                                                              |
| To Shrink size                 | `Shrink desired={size}`                                                                                                                                                           |
# DNS
Set Windows DNS Server: `Set-DnsClientServerAddress -InterfaceIndex 12 -ServerAddress ("172.16.0.10", "172.16.0.21")`

## To create objects in DNS
 
| Description                                                              | Cmdlet                                |
| ------------------------------------------------------------------------ | ------------------------------------- |
| Adds a client subnet to a DNS server.                                    | Add-DnsServerClientSubnet             |
| Adds a conditional forwarder to a DNS server.                            | Add-DnsServerConditionalForwarderZone |
| Creates a DNS application directory partition.                           | Add-DnsServerDirectoryPartition       |
| Adds server-level forwarders to a DNS server.                            | Add-DnsServerForwarder                |
| Adds a primary zone to a DNS server.                                     | Add-DnsServerPrimaryZone              |
| Adds a policy for query resolution to a DNS server.                      | Add-DnsServerQueryResolutionPolicy    |
| Adds a recursion scope on a DNS server.                                  | Add-DnsServerRecursionScope           |
| Adds a resource record of a specified type to a specified DNS zone.      | Add-DnsServerResourceRecord           |
| Adds a type CNAME resource record to a DNS zone.                         | Add-DnsServerResourceRecordCName      |
| Adds an MX resource record to a DNS zone.                                | Add-DnsServerResourceRecordMX         |
| Adds a type PTR resource record to a DNS zone.                           | Add-DnsServerResourceRecordPtr        |
| Adds root hints on a DNS server.                                         | Add-DnsServerRootHint                 |
| Adds a DNS server secondary zone.                                        | Add-DnsServerSecondaryZone            |
| Adds a key signing key (KSK) or zone signing key (ZSK) to a signed zone. | Add-DnsServerSigningKey               |
| Adds a DNS stub zone.                                                    | Add-DnsServerStubZone                 |
| Adds a trust anchor to a DNS server.                                     | Add-DnsServerTrustAnchor              |
| Adds a new delegated DNS zone to an existing zone.                       | Add-DnsServerZoneDelegation           |
| Adds a zone scope to an existing zone.                                   | Add-DnsServerZoneScope                |
| Adds a zone transfer policy to a DNS server.                             | Add-DnsServerZoneTransferPolicy       |
## Configure changes to existing DNS objects
 
| Description                                                    | Cmdlet                                         |
| -------------------------------------------------------------- | ---------------------------------------------- |
| Modifies cache settings for a DNS server.                      | Set-DnsServerCache                             |
| Updates the IP addresses in a client subnet.                   | Set-DnsServerClientSubnet                      |
| Changes settings for a DNS conditional forwarder.              | Set-DnsServerConditionalForwarderZone          |
| Sets debugging and logging parameters.                         | Set-DnsServerDiagnostics                       |
| Changes settings for DNSSEC for a zone.                        | Set-DnsServerDnsSecZoneSetting                 |
| Changes forwarder settings on a DNS server.                    | Set-DnsServerForwarder                         |
| Changes configuration settings for a GlobalNames zone.         | Set-DnsServerGlobalNameZone                    |
| Changes settings for a DNS primary zone.                       | Set-DnsServerPrimaryZone                       |
| Updates settings of a query resolution policy on a DNS server. | Set-DnsServerQueryResolutionPolicy             |
| Modifies recursion settings for a DNS server.                  | Set-DnsServerRecursion                         |
| Modifies a recursion scope on a DNS server.                    | Set-DnsServerRecursionScope                    |
| Changes a resource record in a DNS zone.                       | Set-DnsServerResourceRecord                    |
| Begins aging of resource records in a specified DNS zone.      | Set-DnsServerResourceRecordAging               |
| Enables Response Rate Limiting (RRL) on a DNS server.          | Set-DnsServerResponseRateLimiting              |
| Updates the settings of an RRL exception list.                 | Set-DnsServerResponseRateLimitingExceptionlist |
| Replaces a list of root hints.                                 | Set-DnsServerRootHint                          |
| Changes DNS server scavenging settings.                        | Set-DnsServerScavenging                        |
| Change settings for a DNS secondary zone.                      | Set-DnsServerSecondaryZone                     |
| Modifies DNS server settings.                                  | Set-DnsServerSetting                           |
| Changes settings of a signing key.                             | Set-DnsServerSigningKey                        |
| Changes settings for a DNS server stub zone.                   | Set-DnsServerStubZone                          |
| Configures DNS aging settings for a zone.                      | Set-DnsServerZoneAging                         |
| Changes delegation settings for a child zone.                  | Set-DnsServerZoneDelegation                    |
| Updates a zone transfer policy on a DNS server.                | Set-DnsServerZoneTransferPolicy                |
## Show configuration and parameters of selected DNS object

| Description                                                 | Cmdlet                                         |
| ----------------------------------------------------------- | ---------------------------------------------- |
| Retrieves a DNS server configuration.                       | Get-DnsServer                                  |
| Retrieves DNS server cache settings.                        | Get-DnsServerCache                             |
| Gets client subnets for a DNS server.                       | Get-DnsServerClientSubnet                      |
| Retrieves DNS event logging details.                        | Get-DnsServerDiagnostics                       |
| Gets a DNS application directory partition.                 | Get-DnsServerDirectoryPartition                |
| Gets forwarder configuration settings on a DNS server.      | Get-DnsServerForwarder                         |
| Retrieves DNS server GlobalName zone configuration details. | Get-DnsServerGlobalNameZone                    |
| Gets a global query block list.                             | Get-DnsServerGlobalQueryBlockList              |
| Gets policies for query resolution from a DNS server.       | Get-DnsServerQueryResolutionPolicy             |
| Retrieves DNS server recursion settings.                    | Get-DnsServerRecursion                         |
| Gets the DNS server recursion scopes.                       | Get-DnsServerRecursionScope                    |
| Gets resource records from a specified DNS zone.            | Get-DnsServerResourceRecord                    |
| Displays the RRL settings on a DNS server.                  | Get-DnsServerResponseRateLimiting              |
| Enumerates the RRL exception lists on a DNS Server.         | Get-DnsServerResponseRateLimitingExceptionlist |
| Gets root hints on a DNS server.                            | Get-DnsServerRootHint                          |
| Gets DNS aging and scavenging settings.                     | Get-DnsServerScavenging                        |
| Retrieves DNS server settings.                              | Get-DnsServerSetting                           |
| Gets zone signing keys.                                     | Get-DnsServerSigningKey                        |
| Retrieves DNS server statistics or statistics for zones.    | Get-DnsServerStatistics                        |
| Gets trust anchors on a DNS server.                         | Get-DnsServerTrustAnchor                       |
| Gets trust points on a DNS server.                          | Get-DnsServerTrustPoint                        |
| Gets details of DNS zones on a DNS server.                  | Get-DnsServerZone                              |
| Gets DNS aging settings for a zone.                         | Get-DnsServerZoneAging                         |
| Gets the zone delegations of a DNS server zone.             | Get-DnsServerZoneDelegation                    |
| Gets the scopes of a zone on a DNS server.                  | Get-DnsServerZoneScope                         |
| Gets the zone transfer policies on a DNS server.            | Get-DnsServerZoneTransferPolicy                |