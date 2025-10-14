Get available disks:
Get-Disk | Where-Object PartitionStyle –Eq "RAW"

Initialize disk:
Initialize-disk {number}

Review partition table:
Get-disk

Create a ReFS volume with all available space:
New-Partition -DiskNumber {num} -UseMaximumSize -AssignDriveLetter | Format-Volume -NewFileSystemLabel "NAME" -FileSystem ReFS

Dismount Virtual hard disk:
Dismount-vhd {disk}

Check properties of vhd:
Get-vhd {disk}

Convert VHD to VHDX:
Convert-VHD -Path {disk} -DestinationPath {disk.vhdx}

Change sector size:
Set-VHD –Path {disk} –PhysicalSectorSizeBytes {size}

Optimize .vhdx file:
Optimize-VHD –Path {disk} –Mode Full

## DISKPART
Create new disk using Diskpart:
Diskpart
List disk
Select disk {num}
Convert dynamic
Create volume NAME size={size} disk={num}
Assign letter={letter}
Format

To Extend size:
Extend size {size}

To Shrink size:
Shrink desired={size{

# DNS
Set Windows DNS Server: `Set-DnsClientServerAddress -InterfaceIndex 12 -ServerAddress ("172.16.0.10", "172.16.0.21")`

## To create objects in DNS
 
| Cmdlet                                | Description                                                              |
| ------------------------------------- | ------------------------------------------------------------------------ |
| Add-DnsServerClientSubnet             | Adds a client subnet to a DNS server.                                    |
| Add-DnsServerConditionalForwarderZone | Adds a conditional forwarder to a DNS server.                            |
| Add-DnsServerDirectoryPartition       | Creates a DNS application directory partition.                           |
| Add-DnsServerForwarder                | Adds server-level forwarders to a DNS server.                            |
| Add-DnsServerPrimaryZone              | Adds a primary zone to a DNS server.                                     |
| Add-DnsServerQueryResolutionPolicy    | Adds a policy for query resolution to a DNS server.                      |
| Add-DnsServerRecursionScope           | Adds a recursion scope on a DNS server.                                  |
| Add-DnsServerResourceRecord           | Adds a resource record of a specified type to a specified DNS zone.      |
| Add-DnsServerResourceRecordCName      | Adds a type CNAME resource record to a DNS zone.                         |
| Add-DnsServerResourceRecordMX         | Adds an MX resource record to a DNS zone.                                |
| Add-DnsServerResourceRecordPtr        | Adds a type PTR resource record to a DNS zone.                           |
| Add-DnsServerRootHint                 | Adds root hints on a DNS server.                                         |
| Add-DnsServerSecondaryZone            | Adds a DNS server secondary zone.                                        |
| Add-DnsServerSigningKey               | Adds a key signing key (KSK) or zone signing key (ZSK) to a signed zone. |
| Add-DnsServerStubZone                 | Adds a DNS stub zone.                                                    |
| Add-DnsServerTrustAnchor              | Adds a trust anchor to a DNS server.                                     |
| Add-DnsServerZoneDelegation           | Adds a new delegated DNS zone to an existing zone.                       |
| Add-DnsServerZoneScope                | Adds a zone scope to an existing zone.                                   |
| Add-DnsServerZoneTransferPolicy       | Adds a zone transfer policy to a DNS server.                             |
## Configure changes to existing DNS objects
 
| Cmdlet                                         | Description                                                    |
| ---------------------------------------------- | -------------------------------------------------------------- |
| Set-DnsServerCache                             | Modifies cache settings for a DNS server.                      |
| Set-DnsServerClientSubnet                      | Updates the IP addresses in a client subnet.                   |
| Set-DnsServerConditionalForwarderZone          | Changes settings for a DNS conditional forwarder.              |
| Set-DnsServerDiagnostics                       | Sets debugging and logging parameters.                         |
| Set-DnsServerDnsSecZoneSetting                 | Changes settings for DNSSEC for a zone.                        |
| Set-DnsServerForwarder                         | Changes forwarder settings on a DNS server.                    |
| Set-DnsServerGlobalNameZone                    | Changes configuration settings for a GlobalNames zone.         |
| Set-DnsServerPrimaryZone                       | Changes settings for a DNS primary zone.                       |
| Set-DnsServerQueryResolutionPolicy             | Updates settings of a query resolution policy on a DNS server. |
| Set-DnsServerRecursion                         | Modifies recursion settings for a DNS server.                  |
| Set-DnsServerRecursionScope                    | Modifies a recursion scope on a DNS server.                    |
| Set-DnsServerResourceRecord                    | Changes a resource record in a DNS zone.                       |
| Set-DnsServerResourceRecordAging               | Begins aging of resource records in a specified DNS zone.      |
| Set-DnsServerResponseRateLimiting              | Enables Response Rate Limiting (RRL) on a DNS server.          |
| Set-DnsServerResponseRateLimitingExceptionlist | Updates the settings of an RRL exception list.                 |
| Set-DnsServerRootHint                          | Replaces a list of root hints.                                 |
| Set-DnsServerScavenging                        | Changes DNS server scavenging settings.                        |
| Set-DnsServerSecondaryZone                     | Change settings for a DNS secondary zone.                      |
| Set-DnsServerSetting                           | Modifies DNS server settings.                                  |
| Set-DnsServerSigningKey                        | Changes settings of a signing key.                             |
| Set-DnsServerStubZone                          | Changes settings for a DNS server stub zone.                   |
| Set-DnsServerZoneAging                         | Configures DNS aging settings for a zone.                      |
| Set-DnsServerZoneDelegation                    | Changes delegation settings for a child zone.                  |
| Set-DnsServerZoneTransferPolicy                | Updates a zone transfer policy on a DNS server.                |
## Show configuration and parameters of selected DNS object

| Cmdlet                                         | Description                                                 |
| ---------------------------------------------- | ----------------------------------------------------------- |
| Get-DnsServer                                  | Retrieves a DNS server configuration.                       |
| Get-DnsServerCache                             | Retrieves DNS server cache settings.                        |
| Get-DnsServerClientSubnet                      | Gets client subnets for a DNS server.                       |
| Get-DnsServerDiagnostics                       | Retrieves DNS event logging details.                        |
| Get-DnsServerDirectoryPartition                | Gets a DNS application directory partition.                 |
| Get-DnsServerForwarder                         | Gets forwarder configuration settings on a DNS server.      |
| Get-DnsServerGlobalNameZone                    | Retrieves DNS server GlobalName zone configuration details. |
| Get-DnsServerGlobalQueryBlockList              | Gets a global query block list.                             |
| Get-DnsServerQueryResolutionPolicy             | Gets policies for query resolution from a DNS server.       |
| Get-DnsServerRecursion                         | Retrieves DNS server recursion settings.                    |
| Get-DnsServerRecursionScope                    | Gets the DNS server recursion scopes.                       |
| Get-DnsServerResourceRecord                    | Gets resource records from a specified DNS zone.            |
| Get-DnsServerResponseRateLimiting              | Displays the RRL settings on a DNS server.                  |
| Get-DnsServerResponseRateLimitingExceptionlist | Enumerates the RRL exception lists on a DNS Server.         |
| Get-DnsServerRootHint                          | Gets root hints on a DNS server.                            |
| Get-DnsServerScavenging                        | Gets DNS aging and scavenging settings.                     |
| Get-DnsServerSetting                           | Retrieves DNS server settings.                              |
| Get-DnsServerSigningKey                        | Gets zone signing keys.                                     |
| Get-DnsServerStatistics                        | Retrieves DNS server statistics or statistics for zones.    |
| Get-DnsServerTrustAnchor                       | Gets trust anchors on a DNS server.                         |
| Get-DnsServerTrustPoint                        | Gets trust points on a DNS server.                          |
| Get-DnsServerZone                              | Gets details of DNS zones on a DNS server.                  |
| Get-DnsServerZoneAging                         | Gets DNS aging settings for a zone.                         |
| Get-DnsServerZoneDelegation                    | Gets the zone delegations of a DNS server zone.             |
| Get-DnsServerZoneScope                         | Gets the scopes of a zone on a DNS server.                  |
| Get-DnsServerZoneTransferPolicy                | Gets the zone transfer policies on a DNS server.            |