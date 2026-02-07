# Modes
| **Mode**       | **Command**                                                        |
| -------------- | ------------------------------------------------------------------ |
| privilege EXEC | `enable`                                                           |
| global config  | `configure terminal`                                               |
| line config    | `line console {num}`                                               |
| line VTY       | `line vty {virtual line amount} `({l1} {l2} for multiple lines)    |
| interface      | `interface {interface}` (`range {interface} {n}-{n}` for multiple) |
# Basic Config
## Hostname
1. `enable`
2. `configure terminal`
3. `hostname {name}`
## Banner/MOTD
1. `enable`
2. `configure terminal`
3. `banner motd {indicator}{message}{indicator}` (example: `banner motd #Hello World#`)

# Security
## Passwords
1. **Console**
	1. `enable`
	2. `line config console`
	3. `password {pass}`
	4. `login`
2. **Privilege EXEC**
	1. `enable`
	2. `configure terminal`
	3. `enable secret {pass}`
3. **VTY/Virtual Line**
	1. `enable`
	2. `line config VTY`
	3. `password {pass}`
	4. `login`
4. **Telnet/SSH**
	1. `enable`
	2. `line config VTY`
	3. `password {pass}`
	4. `login`
	5. `transport input ssh telnet`
## Encrypt Stored Passwords
1. `enable`
2. `configure terminal`
3. `service password-encryption`
## Min Password Length
1. `enable`
2. `line config VTY`
3. `security passwords min-length {len}`
## Block login after attempts
1. `enable`
2. `configure terminal`
3. `login block-for {seconds} attempts {num} within {seconds}`
## Logout for inactivity
1. `enable`
2. `configure terminal`/`interface {num}`
3. `exec-timeout {min}{sec}`
## Timeout
1. Go to line you want to add timeout to
2. `exec-timeout {min}{sec}`
## Auto Secure
1. `enable`
2. `auto secure`
## Shutdown Service
1. `enable`
2. `configure terminal`
	1. `no ip htttp server` (shutdown HTTP)
	2. `transport input ssh` (shutdown telnet and only use SSH)
## No Resolving Mistyped Domain Names
1. `enable`
2. `configure terminal`
3. `no ip domain lookup`
## Access Control Lists
1. `enable`
2. `configure terminal`
3. `ip access-list {standard/extended} {name}`
4. **Adding Rules**
	1. `permit {ip} log` ( Logs all traffic from IP)
	2. `permit {protocol} {ip} {wilcard mask} any eq {port}`
5. `exit`
6. **Applying**
	1. `interface {num}`/`line vty {num}`
	2. `ip access-{class/group} {name} {in/out}`
# Configuration
## Save
1. `enable`
2. `copy running-confg startup-config`
## Erase
1. `enable`
2. `erase startup-config`
3. `reload`
## Show
1. `enable`
2. `show running-config`

# Network
## Setting IP address and network info
1. **Router**
	1. `enable`
	2. `interface {interface}`
	3. `description {text}` (Optional)
	4. `ip address {ip}{subnet}` IPv4
	5. `ipv6 address {ip}/{prefix}` IPv6
	6. `no shutdown`
2. **Switch**
	1. `enable`
	2. `line vty {line}`
	3. `description {text}` (Optional)
	4. `ip address {ip}{subnet}` IPv4
	5. `ipv6 address {ip}/{prefix}` IPv6 (Make sure to enable IPv6 first)
	6. `ip default-gateway {ip}`
	7. `no shutdown`

## Enable IPv6 addressing (Switch Only)
1. `enable`
2. `configure terminal`
3. `sdm prefer dual-ipv4-and-ipv6 default`

## Remove IPv6 Address
1. `enable`
2. `interface {interface}`
3. `no ipv6 address {address}/{prefix}`

## MAC Table
1. **Show**
	1. `enable`
	2. `show mac address-table`
2. **Clear**
	1. `enable`
	2. `clear mac address-table`
# Routing
1. **Set IP route**
	1. `enable`
	2. `configure terminal`
	3. `ip route {target network address} {subnet} {Interface IP}`
2. **Enable IPv6 routing**
	1. `enable`
	2. `interface {interface}`
	3. `ipv6 unicast-routing`
3. **Set route delay**
	1. `enable`
	2. `configure terminal`
	3. `delay {milliseconds}`
## Set Domain
1. `enable`
2. `configure terminal`
3. `ip domain name {domain}`

## Enable DHCP
1. `enable`
2. `configure terminal`
3. `ip dhcp database {url}` (Can add `timeout {s}`)

# Debugging
 **All these commands require privilage EXEC mode**

| **Description**             | **Command**                                                                                                                      |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Summary of Interfaces       | `show {ip/ipv6} interface brief`                                                                                                 |
| Routing table (router only) | `show {ip/ipv6} route`                                                                                                           |
| Layer 2 interface info      | `show interface {name}{number}`/`show interface`                                                                                 |
| Layer 3 interface info      | `show {ip/ipv6} interface {name}{number}`/`show {ip/ipv6}                                                                        |
| Show used ports:            | `show ip ports all`/`show control-plane host open-ports`                                                                         |
| Show list of known hosts:   | `show arp`                                                                                                                       |
| Show operation protocols    | `show protocols`                                                                                                                 |
| Show version                | `show version`                                                                                                                   |
| Show CDP neighbors          | `show cdp neighbor`                                                                                                              |
| Debugging logs              | `debug {idk} (example: debug ip icmp)`<br>`no debug {idk}`<br>`undebug {idk}`<br>`undebug all`                                   |
| Terminal logs               | `terminal monitor (allow for debug messages to be shown)`<br>`terminal no monitor (opposite)`                                    |
| VLAN                        | `show vlan brief`<br>`show interfaces trunk`<br>`show interfaces switchport`<br>`show interfaces status`<br>`show spanning-tree` |
# SSH
1. Configure Hostname
2. Configure IP domain name
3. Generate key to encrypt SSH traffic
	1. `enable`
	2. `configure terminal`
	3. `crypto key generate rsa general-keys modulus {size}`
4. Verify or create a local database entry
	1. `username {name}`/`username {name} secret {pass}`
5. Authenticate against the local database
	1. `line vty {num}`
	2. `login local`
6. Enable vty inbound SSH sessions
	1. `line vty {num}`
	2. `transport input {ssh/telnet}`
## Change SSH Version
1. `enable`
2. `configure terminal`
3. `ip ssh version {1/2}`

# VLAN
## Add vlan to vlan database in switch
1. `enable`
2. `configure terminal`
3. `vlan 10`
## Name the vlan
1.  `name {name}`
## Configure port to be an access port for a specific vlan.
1. `enable`
2. `configure terminal`
3. `interface {interface} {number}`
4. `switchport mode access` (Sets port as an access port)
5. `switchport access {name}` (Sets designated port as member of vlan)
## Configure a trunk port
1. `enable`
2. `configure terminal`
3. `interface {interface} {number} `
4. `switchport trunk encapsulation dot1q` (If support of ISL method)
5. `switchport mode trunk`
## Native vlan
**default is vlan 1**
1. `enable`
2. `configure terminal`
3. `switchport trunk native {name}`
## Allowed vlan list (kinda like a firewall ig)
**By default all traffic from vlans in the database is forwarded out the trunk port**
1. `enable`
2. `configure terminal`
3. `interface {interface} {number} `
4. `switchport trunk allowed vlan {n1,n2}`
 5. `switchport trunk allowed vlan add {n} `(to add after setting, can also use remove)

# AAA
## Config new AAA log
1. `aaa new-model`
## Set AAA as log
**"local-case" uses case sensitive usernames**
1. `aaa authentication login <default/SSH-METHOD> local-case`
## Create username and password locally
1. `username <name> algorithm-type scrypt secret <pass>`
## Set AAA log method for vty
1. `line vty <lines>`
2. `login authentication <default/SSH-METHOD>`
## Apply max limit for pass
1. `aaa local authentication attempts max-fail <amount>`