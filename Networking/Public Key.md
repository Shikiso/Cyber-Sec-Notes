# Digital Signature
A digital signature is similar to a normal signature. However instead of a scribble a mathematical technique is used to provide a non-repeatable signature.  These signatures have specific properties that ensure authentication and data integrity.
(Digital signatures use asymmetric cryptography)

Digital signatures are commonly used in:
- Code signing - Verifying the integrity of execrable files.
- Digital certificates - Used to identify the system with a vendor website.

There are three Digital Signature Standard (DSS) algorithms that are used for generating and verifying digital signatures:

- **Digital Signature Algorithm (DSA)** - DSA is the original standard for generating public and private key pairs, and for generating and verifying digital signatures.
- **Rivest-Shamir Adelman Algorithm (RSA)** - RSA is an asymmetric algorithm that is commonly used for generating and verifying digital signatures.
- **Elliptic Curve Digital Signature Algorithm (ECDSA)** - ECDSA is a newer variant of DSA and provides digital signature authentication and non-repudiation with the added benefits of computational efficiency, small signature sizes, and minimal bandwidth.

## Example scenario (from netacad)
Bob is confirming an order with Alice. Alice is ordering from Bob’s website. Alice has connected with Bob’s website, and after the certificate has been verified, the Bob’s certificate is stored on Alice’s website. The certificate contains Bob’s public key. The public key is used to verify the Bob’s digital signature.

(Refer to the figure to see how the digital signature is used).
![](/Images/digital_signature_1.png)
When Alice receives the digital signature, the following process occurs.
![](/Images/digital_signature_2.png)

# Authorities and PKI Trust System
## Public Key Management
When two hosts are establishing an asymmetric connection, they will exchange their public key information.

For example, an SSL certificate is a digital certificate that confirms the identity of a website domain. To implement SSL on your website, you purchase an SSL certificate for your domain from an SSL Certificate provider. The trusted third party does an in-depth investigation prior to the issuance of credentials. After this in-depth investigation, the third-party issues credentials (i.e. digital certificate) that are difficult to forge. From that point forward, all individuals who trust the third party simply accept the credentials that the third-party issues.

When computers attempt to connect to a web site over HTTPS, the web browser checks the website’s security certificate and verifies that it is valid and originated from a reliable Certificate Authority (CA). This validates that the website identify is true. The digital certificate is saved locally by the web browser and is then used in subsequent transactions. The website’s public key is included in the certificate and is used to verify future communications between the website and the client.

Think of it like a drivers license. The government issues you one and everyone trusts the information on it since the government issued it.

## Public Key Infrastructure (PKI)
PKI is used to support large-scale distribution and identification of public encryption keys.
Here is an example of a PKI certificate being used:
![](/Images/PKI.png)
(Not all PKI certificates are directly received from a CA. A registration authority (RA) is a subordinate CA and is certified by a root CA to issue certificates for specific uses.)

## Authorities System
CAs use different classes when providing a certificate. 0 being the least trusted and 5 the most.

| Class | Description                                                                                                              |
| ----- | ------------------------------------------------------------------------------------------------------------------------ |
| 0     | Used for testing in situations in which no checks have been performed.                                                   |
| 1     | Used by individuals who require verification of email.                                                                   |
| 2     | Used by organizations for which proof of identify is required.                                                           |
| 3     | Used for servers and software signing. Independent verification and checking of identity and authority is done by the CA |
| 4     | Used for online business transactions between companies.                                                                 |
| 5     | Used for private organisations or government security.                                                                   |

## Trust System
PKIs can form different typologies of trust. The simplest is the single-root PKI topology.
![[/Images/single-root_pki.png]]
On larger network PKI CAs may be linked using two basic architectures:

**Cross-certified CA topologies** - A peer-to-peer model in which individual CAs establish trust relationships with other CAs by cross-certifying CA certificates.
![[/Images/corss-certified_ca.png]]

**Hierachical CA** - Highest level CA is called the root. It can issue certificates to end users and to subordinate CA.
![[/Images/hierachical_ca.png]]
