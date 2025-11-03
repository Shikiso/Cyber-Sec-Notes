# Internet Key Exchange
The Internet Key Exchange protocol is a key management protocol standard. It is used in conjunction with the IPsec standard. IKE automatically negotiates IPsec security associations and enables IPsec secure communications. IKE enhances IPsec by adding features and simplifies configuration for the IPsec standard.

IKE is a [hybrid protocol](/Networking/Protocols.md) that implements key exchange protocols inside the Internet Security Association Key Management Protocol (ISAKMP) framework.
ISAKMP defines:
- Message format
- Mechanic of a key exchange protocol
- Negotiation process to build an SA for IPsec

Instead of transmitting keys directly across a network IKE calculates shared keys based on the exchange of a series of data packets. This disables a third party from decrypting the keys even if the third party captured all of the exchange data that was used to calculate the keys. IKE uses UDP port 500 to exchange IKE information between the security gateways. UDP port 500 packets must be permitted on any IP interface that is connecting a security gateway peer.

# Phases
IKE uses ISAKMP for phase 1 and 2 of key negotiation.
Phase 1 negotiates a security associations (a key) between two IKE peers.
The key negotiated in phase 1 enables IKE peers to communicate securely in phase 2. During phase 2 negotiation IKE establishes keys for other applications such as IPsec.

## Phase 1
Two IPsec peers perform initial negotiation of SAs (key). The basic purpose of phase 1 is to negotiate ISAKMP policy, authenticate the peers and set up a secure tunnel between the peers. The tunnel will then be used in Phase 2 to negoitate the IPsec policy, shown in the image.

![](/Images/negotiate_ipsec_policy.png)
Phase 1 can be implements in main or aggressive mode. When main mode is used the identities of the two IKE peers are hidden.
Aggressive mode takes less time than main mode to negotiate keys between peers. However since the authentication hash is sent unencrypted before the tunnel is established aggressive mode is vulnerable to a brute-force attack.

Think of Phase 1 as setting up the connection using SA over a WAN networking. (This means using WAN interfaces).

(IKE policy and ISAKMP policy are equivalent.)

## Phase 2 (Quick Mode)
Phase 2 negotiates the IPsec security parameters that will be used to secure the IPsec tunnel. This is already protected by the existing IKE SA from phase 1.

SAs are negotiated by the IKE process ISAKMP on behalf of IPsec, which needs encryption keys for operation. This is done when the SA lifetime expires. A Diffie-Hellman exchange can be performed for addition security.

Quick mode provides Relay Protection through exchange of nonces. A new Diffie-Hellman exchange is created with each Quick Mode.

Phase 2 is everything that is private such as building the routing and network communications between private networks. (Essential LAN to LAN stuff)
