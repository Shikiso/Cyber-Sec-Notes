# How does DNS name resolution work?
TCP/IP set of protocols identify sources by their destination IP address. However people have a hard time remembering numbers. So we use names instead. Administrators assign names to computers then link these names to the computer IP addresses in a name resolution system such as DNS. These names are in host name format, for example dc1.contosos.com.

## Host names
A host name is a computer name that is added to a domain name and top level domain to make a fully qualified domain name (FQDN).
![](/Images/FQDN.png)
When creating a host name their are some things to remember:
- Select computer names that are easy to remember
- Identify the owner of the computer in the name
- Select names that describe the purpose of the device
- Match the active directory domain name to the primary DNS suffix of the computer name
- Make sure the name is unique

# Host names are resolved on the Internet
A name resolution client query can take many paths, depending on if it's public or private and how the DNS infrastructure is designed. There are 13 root servers on the Internet that are responsible for managing the overall structure of DNS resolution. When you register a domain name on the Internet you're paying to be apart of this system.
The name resolution process for the name www.microsoft.com is:
1. A workstation queries the local preferred DNS server for the IP address.
2. If the local DNS server does not have the information, it queries a root DNS server for the location of the .com DNS servers.
3. The local DNS server queries a .com DNS server for the location of microsoft.com DNS servers.
4. The local DNS server returns the IP address of www.microsoft.com to the workstation.

You can add forwarding so the local DNS server sends the request to another DNS server instead of querying the root server. Or add caching so results are stored for a set time making the process quicker.

# DNS Components
## DNS naming structure
DNS namespace is a hierarchical naming structure meaning it starts with the root domain. The root domain itself can have subdomains under it. The domain names can either be public (internet facing) or private. If they are private you can decide how to define your namespace. But if its public you must work with the Inter Corporation for Assigned Names and Numbers (ICANN) or other internet naming registration authorities.

DNS has a unique namespace, indicated by an empty string space. Preceding this is a single dot. Below this in the public namespace is one of the several other top-level domain namespaces. There are 3 kinds of top-level domains in the public namespace:
- Organisations (.com, .net, .edu, .org)
- Geographical (.au, uk, .de)
- Reverse domains (these are in the name.name format, addr.arpa, ip6.arpa)

## DNS Server
Contains a database of host names and IP address. Responding to client requests and providing required mapping information. It can cache information for other domains and can also forward DNS client requests to another DNS server.

### DNS Zone & Records
A DNS infrastructure is broken up into zones each allocated a DNS server to own. For example a DNS server might be responsible for paris.europe.microsoft.com DNS zone and another for berlin.europe.microsoft.com.
Types:
- Forward lookup zone: Resolves host names to IP addresses
- Reverse lookup zone: Resolves IP addresses to host names

### Resource Records
The DNS zone file stores resource records. Which specify a resource type and the IP address to locate the resource. The most common resource record being a host resource record. This is a simple record that resolves a host name to an IP address.
The following table describes the most common resource records.

| **DNS resource records**                 | **Description**                                                                                                                                            |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Start-of-authority (SOA) resource record | The record identifies the primary name server for a DNS zone, in addition to other specifics, such as Time to Live (TTL) and refresh.                      |
| Host address (A) resource record         | The main record that resolves a host name to an IPv4 address.                                                                                              |
| Canonical name (CNAME) resource record   | An alias record type that maps one name to another (for example, [www.microsoft.com](http://www.microsoft.com/) is a CNAME of the A record microsoft.com). |
| MX resource record                       | The record is used to specify an email server for a particular domain.                                                                                     |
| SRV resource record                      | The record identifies a service that is available in the domain. Active Directory uses these records extensively.                                          |
| Name server (NS) resource record         | The record identifies a name server for a domain.                                                                                                          |
| AAAA                                     | The main record that resolves a host name to an IPv6 address.                                                                                              |
| Pointer (PTR) resource record            | The record is used to look up and map an IP address to a domain name. The reverse lookup zone stores the names.                                            |
# Configure DNS Client
You can configure the DNS client settings on a Windows machine by going to the settings and for each network adapter and specify the DNS server address.
![](/Images/WIN_DNS_client.png)
Powershell - `Set-DnsClientServerAddress -InterfaceIndex 12 -ServerAddress ("172.16.0.10", "172.16.0.21")`

For a Windows Server you would need to preform these steps:
1. In Server Manager, click the **Local Server**, and then click the appropriate network adapter in the **Properties** section.
    
2. Right-click the network adapter for which you are configuring DNS, and then click **Properties**.
    
3. In the **Properties** window, click the appropriate TCP protocol stack, and then click **Properties**.
    
4. In the appropriate TCP protocol stack **Properties** window, select **Use the following DNS server addresses**, and then in the **Preferred DNS server** and **Alternate DNS server** text boxes, type the IP address of the DNS servers.

5. Optionally, you can add additional DNS server addresses and change the priority order for DNS servers by clicking **Advanced**, and then clicking the **DNS** tab in the **Advanced TCP/IP Settings** window. These advanced settings include several options or DNS suffix settings. The DNS suffix of a client specifies the domain namespace in which the client operates. You can also add additional DNS suffixes to enable the client to resolve single-label names for DNS names that exist in other DNS namespaces. Additionally, the advanced settings include the default behavior for the client to register its addresses in DNS, through the check box **Register this connection’s addresses in DNS**_._
# Configuring Zones
### Creating Records in DNS
You must create DNS resource records before they can be referenced within the DNS infrastructure. Once a DNS resource record is created is exists within a DNS zone.
There are 2 ways to create A resource record:

**Dynamic creation** is when dynamic updates are allowed for a DNS zone. Client that use DNS will register with the DNS server and then the resource records for each client are create automatically.

**Manual creation** is used then dynamic updates are not enabled and you need to create resource records manually. Even when dynamic updates is enabled you need to create some records manually.

### Creating DNS records
To create a resource record in the GUI, perform the following steps:

1. Open the **DNS Manager** console.
2. Locate the zone for which you are creating the record.
3. Right-click the zone, and then click one of the following: **New Host**, **New Alias**, **New Mail Exchanger**, or **Other New Records**.
4. Type a host name for the new record, and fill in the other details for the record, depending on the record type.

You can also create host records by using the following Windows PowerShell cmdlets for DNS:
- `**Add-DnsServerResourceRecord**. Creates any resource record, specified by type.`
- `**Add-DnsServerResourceRecordA**. Creates a type A resource record.`
- `**Add-DnsServerResourceRecordCNAME**. Creates a CNAME alias resource record.`
- `**Add-DnsServerResourceRecordMX**. Creates an MX resource record.`
- `**Add-DnsServerResourceRecordPtr**. Creates a PTR resource record.`

For example, the following command uses the **Add-DNSServerResourceRecordA** cmdlet to add the host name **LON-SVR3** to the Adatum.com zone for the IP address 172.16.0.24.
`Add-DNSServerResourceRecordA –Name “LON-SVR3” –ZoneName “Adatum.com” –IPv4Address “172.16.0.24”`
![](/Images/DNS_record.png)
Powershell - `Add -DnsServerResourceRecordA -ZoneName Contoso.com -Name ATL-SVR1 -IpAddress 172.16.18.25`

# Configuring DNS Zones
You can host DNS resource records on more than one DNS server. A DNS zone contains DNS records for one or more namespaces. You can replicate zone data to more than one server adding redundancy to the zone. If a zone hosts critical server resource records this zone is likely to have a higher level of redundancy than a zone that defines noncritical devices.

## Forward Lookup Zones
A forward lookup zone resolves host names to IP addresses and hosts the common resource records: A, CNAME, SRV, MX, SOA, TXT, NS. This zone must exist for a DNS zone to be considered authoritative. 
Client sends host names or FQDNs of the DNS servers domain to the DNS server
The DNS server uses the FQDN to look up a corresponding IP address or to find any source record type that the client prescribes such as a domain controllers SRV records.
The DNS server returns the IP address or addresses to the client in the DNS response.

## Reverse Lookup Zones
A reverse lookup zone resolved IP address to a domain name and hosts start of authority (SOA), name server (NS) and pointer (PTR) resource records. A reverse lookup zone returns the host name given a particular IP address.

### Primary/Secondary Zones
| Zones                       | Description                                                           |
| --------------------------- | --------------------------------------------------------------------- |
| Primary                     | Read/Write copy of a DNS database                                     |
| Secondary                   | Read-only copy of a DNS database                                      |
| Stub                        | Copy of a zone that contains only records used to locate name servers |
| Active Directory-Integrated | Zone data is stored in AD DS rather than in zone files                |

# Configuring Name Resolution Between DNS Zones
## Resolving DNS names between Zones
![](/Images/resolving_dns_zones.png)When a DNS name resolves on the internet an entire system of computers is used rather than just a single server. There are hundred of servers on the internet, called root servers which manage the overall practice of DNS resolution.

# DNS Caching
DNS caching increases the performance of an organizations DNS by decreasing the time it takes to resolve a DNS host name. When a DNS server resolves a DNS name it adds the name to its cache. Over time this builds a cache of domain names and their associated IP addresses for the most common domains that the organization uses.

# DNS Forwarding
DNS forwarding provides a way for namespaces or resource records not contained in a DNS servers zone to be passed on to another DNS server for resolution. 

### Configuring forwarding 
You can configure forwarders on a DNS server by using the following steps: 
1. In the DNS Manager console, right-click the DNS server name, and then click Properties. 
2. On the Forwarders tab, click Edit, and then add DNS servers that can be used to forward DNS queries for external DNS names.