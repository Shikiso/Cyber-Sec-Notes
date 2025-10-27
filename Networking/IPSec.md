(This is apart of VPN but it's a lot so I moved it into a separate file)

IPSec is an IETF standard that defines how a VPN can be secured across IP networks. IPSec can protect traffic from Layer 4 to 7. IPSec is not bound to any specific rules allowing it to integrate new technologies without updating existing standards.

Using the IPsec framework, IPsec provides these essential security functions:
- **Confidentiality** - IPsec uses encryption algorithms to prevent cyber criminals from reading the packet contents.
- **Integrity** - IPsec uses hashing algorithms to ensure that packets have not been altered between source and destination.
- **Origin authentication** - IPsec uses the Internet Key Exchange (IKE) protocol to authenticate source and destination. Methods of authentication include the use of pre-shared keys (passwords), digital certificates, or RSA certificates.
- **Diffie-Hellman** - Secure key exchange typically using various groups of the DH algorithm.
The open slots show below can be filled with any of the choices available for that IPsec function to create a unique security association (SA).
![](/Images/ip_sec_sa.png)

## IPSec Protocol Encapsulation
IPSec encapsulates packets using Authentication Header (AH) or Encapsulation Security Protocol (ESP).
![](/Images/ipsec_protcol_encap.png)
## Confidentiality
Confidentiality is achieved by encrypting the data. The degree of confidentiality depends on the encryption algorithm and the length of the key used in the encryption algorithm.
![](/Images/ipsec_encryption.png)
The options are in order of least to most secure, DES, 3DES, AES and SEAL.
- DES uses a 56-bit key and should be avoided.
- 3DES is a variant of the 56-bit DES. It uses three independent 56-bit encryption keys per 64-bit block, which provides significantly stronger encryption strength over DES. 
- AES is the most recommended symmetric encryption algorithm. It provides stronger security than DES and is computationally more efficient than 3DES. AES offers three different key lengths: 128 bits, 192 bits, and 256 bits.
- SEAL is a stream cipher, which means it encrypts data continuously rather than encrypting blocks of data. SEAL uses a 160-bit key and is considered to be very secure.
## Integrity
Data Integrity means the data received is the same as the data that was sent. Potentially data could be intercepted and modified. Because of this a hashing algorithm used. (If using SHA use SHA-256 for integrity).
![](/Images/ipsec_integrity.png)
## Authentication
Since we need to be secure when using a VPN we must know who is one the other end. 
![[ipsec_authentication.png]]
This is done by having the local device, the authentication key and identity information sent through a hash algorithm to from the hash for the local peer (Hash_L). If the remote device can independently create the same hash, the local device is authenticated. Once this is done the same happens for the remote device.
### PSK Authentication
![](/Images/PSK_authentication.png)
### RSA Authentication
![](/Images/rsa_authentication.png)
## Diffie-Hellman
Encryption algorithms require a symmetric, shared secret key to perform encryption and decryption. The easier key exchange method is to use a public key exchange method such as Diffie-Hellman. (Diffie-Hellman 1 is least secure and 24 is the most. Higher number better security).
[Youtube vid from Computerphile](https://www.youtube.com/watch?v=NmM9HA2MQGI&pp=ygUNZGlmZmUtaGVsbG1hbg%3D%3D)

# IPSec Protocols
The main protocols are Authentication Header (AH) and Encapsulation Security Protocol (ESP). AH uses IP protocol 51 and is appropriate only when confidentiality is not required. It provides data authentication and integrity but no confidentiality. ESP uses IP protocol 50 and provides both confidentiality and authentication.
## Authentication Header
AH achieves authenticity by applying a keyed one-way hash function to the packet to create a hash or message digest. The hash is combined with the text and is transmitted in plain text. The receiver detects changes in any part of the packet that occurs during transit by performing the same one-way hash function on the received packet and comparing the result to the value of the message digest that the send supplied. Authenticity is assured because the on-way hash also employs a shared secret key between two systems.

The AH function is applied to the entire packet, except for an IP header fields that normally change in transit.

## AH process
1. IP header and data payload are hashed using the shared secret key.
![](/Images/ah_process_1.png)
2. The hash builds a new AH header, which is inserted into the original packet.
![](/Images/ah_process_2.png)
3. The new packet is transmitted to the IPsec peer router
4. The peer router hashes the IP header and data payload using the shared secret key, extracts the transmitted hash from the AH header, compares the two hashes.
![](/Images/ah_process_3.png)
The hashes must match exactly. If one bit is changed in the transmitted packet, the hash output on the received packet changes and the AH header will not match.

AH supports MD5 and SHA algorithms. AH may not work if the environment uses NAT.

## Encapsulation Security Protocol
If ESP is selected as the IPsec protocol an encryption algorithm must be selected.

ESP can also provide integrity and authentication. 
1. First the payload is encrypted
2. The encrypted payload is sent through a hash algorithm
3. The hash provides authentication and data integrity for the data payload

ESP can also enforce anti-reply protection. Anti-Replay protection verifies that each packet is unique and is not duplicated.

## ESP Encrypts and Authenticates
When both authentication and encryption are selected, encryption is performed first. The reason for this is that it makes it easier for rapid detection and rejection of replayed or fake packets by the receiving device. Prior to decryption the packet the receiver can authenticate inbound packets. Allowing for quicker detection of problems or attacks.
![](/Images/esp_encap.png)
## Transport and Tunnel Modes
ESP and AH can be applied to IP packets in two different modes, transport mode and tunnel mode.
![](/Images/transport_tunnel_mode.png)
### Transport Mode
- Security provided only for transport layer and above
- Protects payload but leaves original IP in plain text
- Original IP used to route the packet through internet
- Used between hosts
### Tunnel Mode
- Provides security for complete original IP packet
- Original Packet is encrypted than encapsulated in another IP packet (this is IP-in-IP encryption)
- IP address on outside is used to route the packet through the internet
- Used between a host and security gateway or between two security gateways

For host to gateway applications a home office router might not be able to perform IPsec encapsulation + encryption. In this case the client performs the IPsec IP-in-IP encapsulation + encryption.

For gateway to gateway applications the security gateways perform the IP-in-IP encryption + encapsulation.

As show in the image transport mode provides authentication and integrity for the entire packet but does not encrypt.
Tunnel mode encapsulates the IP packet with an AH and new IP header and signs the entire packet for integrity and authentication.
![](/Images/tunnel_transport_packet.png)
