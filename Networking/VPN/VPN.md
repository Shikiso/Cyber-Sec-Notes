# Virtual Private Network

A VPN is used to secure network traffic between sites and users. Organisations use VPNs to create end-to-end private network connections.

# Topologies
## Site-to-Site
Used to connect networks across another untrusted network such as the internet.
The end hosts send and receive unencrypted TCP/IP traffic through a VPN-terminating device.
A site-to-site VPN is created when VPN terminating devices (also called VPN gateways) are preconfigured with information to establish a secure tunnel.
- Traffic is only encrypted between devices
- Internal hosts have no idea that a VPN is being used

![](/Images/VPN2.png)

## Remote-Access
A remote-access VPN is dynamically created to establish a secure connection between a client and a VPN terminating device.
Example: A remote access SSL VPN is used when you check your banking information online.
![](/Images/VPN1.png)

## Secure Socket Layer (SSL)
SSL uses public key infrastructure and digital certificates to authenticate peers.
Both IPsec and SSL VPN technologies offer access to any network application or resource.
(IPsec is better when security is a concern)

| Feature               | IPsec                                                          | SSL                                                                          |
| --------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------------------- |
|                       | Works at Layer 3 (Network layer)                               | Works at Layer 7 (Application layer), encrypting HTTP traffic not IP packets |
| Connection complexity | Requires a VPN client pre-installed on host                    | Only requires a web browser on host                                          |
| Connection option     | Only specific devices with specific configurations can connect | Any device with a web browser can connect                                    |
## Site-to-Site IPsec
Site-to-site VPNs are used to connect networks across another untrusted network such as the internet. End hosts send and receive normal unencrypted TCP/IP traffic through a VPN-terminating device. 
The VPN-terminating device is typically called a VPN gateway. A VPN gateway device could be a router or firewall.
![](/Images/site-to-site_vpn.png)
The VPN gateway encapsulates and encrypts outbound traffic. It then sends the traffic through a VPN tunnel over the internet to a VPN gateway at the target site. Upon receiving the VPN gateway strips the header, decrypts the content and relays the packet as normal.

