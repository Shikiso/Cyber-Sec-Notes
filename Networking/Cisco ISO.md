
(FOR BOTH SWITCH AND ROUTER UNLESS SAYS OTHERWISE)	

## Modes
| Mode           | Command                                                        |
| -------------- | -------------------------------------------------------------- |
| privilege EXEC | enable                                                         |
| global config  | configure terminal                                             |
| line config    | line console 0                                                 |
| line VTY       | line vty {virtual line amount} ({l1} {l2} for multiple lines)  |
| interface      | interface {interface} (range {interface} {n}-{n} for multiple) |

## Basic Config
Hostname:
	- privilage EXEC
	- global config
	- hostname {name}

Banner:
	- privilage EXEC
	- global config
	- banner motd {indicator} {message} {indicator}

Backup Config (https://www.cisco.com/c/en/us/support/docs/ios-nx-os-software/ios-software-releases-122-mainline/46741-backup-config.html):
	- privilege EXEC
	- copy running-config tftp

## Config Passwords
Console:
	- privilage EXEC
	- line config console
	- password {pass}
	- login

privilege EXEC:
	- privilege EXEC
	- global config
	- enable secret {pass}

VTY:
	- privilege EXEC
	- line config VTY
	- password {pass}
	- login

Telnet/SSH:
	- line config VTY
	- password password
	- login
	- transport input ssh telnet

Encrypt:
	- privilege EXEC
	- global config
	- service password-encryption
## Configuration
Save:
	- privilege EXEC
	- copy running-config startup-config

Erase:
	- privilege EXEC
	- erase startup-config
	- reload

Show:
	- privilege EXEC
	- show running-config

Timeout:
	- specific line you want to timeout/privilege EXEC
	- exec-timeout {min} {sec}
## Network

Setting SWITCH:
	- privilege EXEC
	- virtual lan interface
	- ip address {ip} {subnet}    {- Sets IPv4 address
	- ip default-gateway {ip}      {- Sets default gateway
	- no shutdown	             {- Enables interface

Setting ROUTER:
	- privilage EXEC
	- interface mode
	- desciption {text}
	- ip address {ip} {subnet}	{- Sets IPv4 address
	- ipv6 address {ip}/{prefix} 	{- Sets IPv6 address
	- no shutdown	             	{- Enables interface

Show MAC table:
	- privilage EXEC
	- show mac address-table

Clear MAC table:
	- privilage EXEC
	- clear mac address-table

IP routes:
	- global config
	- ip route {Target network IP address} {subnet} {Interface IP}
	(To set anywhere else go here use 0.0.0.0 as IP and subnet)

Enable ipv6 routing ROUTER (Enables router to forward IPv6 packets):
	- privilage EXEC
	- interface mode
	- ipv6 unicast-routing

Enable ipv6 SWITCH:
	- privilege EXEC
	- global config
	- sdm prefer dual-ipv4-and-ipv6 default

Remove ipv6 address:
	- privilege EXEC
	- interface mode
	- no ipv6 address {address}/{prefix}

Set domain:
	- global config
	- ip domain name {domain}

Setting delay: (Used to make certain paths more attractive to routers when deciding a path)
	- global config
	- delay {amount in ms}

Setup DHCP:
	- global config
	- ip dhcp database {url} (optional timeout {s})
## Debug

Summary of interfaces:
	- privilage EXEC
	- show {ip/ipv6} interface brief

Routing table ROUTER:
	- privilege EXEC
	- show {ip/ipv6} route

Layer 2 interface info:
	- privilege EXEC
	- show interface {name}{number}	{- Specific
	- show interface		{- All

Layer 3 interface info:
	- privilege EXEC
	- show {ip/ipv6} interface {name}{number}	{- Specific
	- show {ip/ipv6} interface			{- All

Show used ports:
	- privilege EXEC
	- show ip ports all
	- (for older devices) show control-plane host open-ports

Show running config:
	- show running-config

Show list of known hosts:
	- show arp

Show operational protocols:
	- show protocols

Show version:
	- show version

Show CDP neighbors:
	- show cdp neighbor

Debugging:
	- debug {idk} (example: debug ip icmp)
	- no debug {idk} ({- off ^on)
	- undebug {idk} ({- also off)
	- undebug all ({- all off)

Terminal log messages: (by default debug is not displayed on remote connections)
	- terminal monitor (allow for debug messages to be shown)
	- terminal no monitor (opposite)

VLAN show commands:
	- show vlan brief
	- show interfaces trunk
	- show interfaces switchport
	- show interfaces status
	- show spanning-tree
## Security
Automatically Secure:
	- privilege EXEC
	- auto secure

Set minimum password length:
	- Line vty
	- security passwords min-length {length}

Block after attempts:
	- global config
	- login block-for {seconds} attempts {attempts} within {seconds}

Logout inactivity:
	- interface/global config
	- exec-timeout {min} {sec}

Shutdown port:
	- global config
	- no ip http server (shutdown http)
	- transport input ssh (shutdown telent by only using SSH)

Prevent resolving mistyped domain names:
	- global config
	- no ip domain lookup

Creating access control list (use access-class for VTY and access-group for interface):
	- global config
	- ip access-list {standard/extended} {name} {- Creating access list
	- Add your rules:
		- permit {ip} log {- log just logs all traffic from ip
		- permit {protocol} {ip} {wildcard mask} any eq {port} {- don't need every thing
		- remark This is a comment
	- Example:
		- permit 192.168.10.0 log
		- permit tcp 192.168.0.0 0.0.0.255 any eq 443
	- exit

Apply access control list (use access-class for VTY and access-group for interface):
	- interface/vty
	- ip access-{class/group} {name} {in/out}
		
## Secure Shell
1. Configure Hostname
2. Configure IP domain name
3. Generate key to encrypt SSH traffic
	- global config
	- crypto key generate rsa general-keys modulus {size in bits 360-2048}
4. Verify or create a local database entry
	- global config
	- username {name} | username {name} secret {pass}
5. Authenticate against the local database
	- line vty
	- login local
6. Enable vty inbound SSH sessions
	- line vty
	- transport input {ssh|telent}

Change ssh version
	- global config
	- ip ssh version {1/2}
## VLAN
Add vlan to vlan database in switch
	- global config
	- vlan 10

Name the vlan
	- name {name}

Once the vlan is added into the database you can then configure a port to be
an access port for a specific vlan.
	- global config
	- interface {interface} {number}
	- switchport mode access (Sets port as an access port)
	- switchport access {name} (Sets designated port as member of vlan)

A trunk port is a port that carries multiple vlans
	- global config
	- interface {interface} {number} 
	- switchport trunk encapsulation dot1q (If support of ISL method)
	- switchport mode trunk

Native vlan is the one vlan on a trunk port which is allowed to remain untagged (default is vlan 1)
	- global config
	- switchport trunk native {name}

Allowed vlan list (kinda like a firewall ig)
By default all traffic from vlans in the database is forwarded out the trunk port
	- global config
	- interface {interface} {number}
	- switchport trunk allowed vlan {n1,n2}
	- switchport trunk allowed vlan add {n} (to add after setting, can also use remove)
