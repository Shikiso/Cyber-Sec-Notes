C.I.A triad is regarded as the most valid model of security.
It includes three different main principles, those being confidentiality, integrity and availability. These three principles are required for ensuring the security of any system.

# Confidentiality
Ensures no individual can view or access resources without authorization

The most common ways of maintaining confidentiality are:
- **Steganography**: A technique for hiding any piece of important info in the form of a simple image or text
- **Cryptography**: A technique of encryption and decryption using secretive keys
- **Access  control**: Prevents any form on unauthorized access 

# Integrity
Assurance of completeness and trustworthiness and accuracy of information.

Three primary ways in which organizations ensure the integrity of their data are:
- **Hashing**: Combining the function of hash along with a secret key which is shared
- **Validation of Input**: Validating or also restricting those values which are entered by the users.
- **Digital Signature**: Mathematics that ensures there is no type of alteration or modification in the sent message.

# Availability
Ensure resources you want available are available and can be used in a efficient manner without compromising the security.

# Other
Elements that directly support the same goal as the CIA triad.
## Identification
Using some kind of identifier such as a username or password or a smart card to access a system.
Providing user credentials is known as identification and is the first step in authentication.
## Authentication
Once credentials have been provided they must be authenticated. So that we know the person is who they say they are. Credentials must be validated by what ever system is in place such as comparing the hash of two passwords.
## Authorization
Even if you have be identified and authenticated, you may not have full access to a system. This is because you do not have authorization for certain tasks. Authorization is the process of granting users  or entities that appropriate permissions, right and privileges to the system.
## Auditing and Accountability
Even when users are authenticated they may still try to access parts of a system they do not have permission to access. Administrators want to know when these incidents occur since they could be related to potential attempts at privilege escalation. Auditing is implementing recordings of the users or other entities actions when interacting with the system or data.

Accountability is the process of holding users accountable for their actions. Deterring honest users from committing security policy violations and punishing users who disregard these policies.
## Non-repudiation
Non-repudiation means that users cannot deny that they have performed an action with no regard to the system or data. It is the function of auditing and accountability since it allows security admins to not only detect when unauthorized actions have occurred but to trace those actions back to an individual.