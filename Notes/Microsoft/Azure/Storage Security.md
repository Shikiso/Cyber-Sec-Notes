Common strategies:
- Encryption
- Authentication
- Authorization
- User access control
- File permissions
- Private signatures

![](/Images/storage_sec_azure.png)

- **Encryption at rest**. Storage Service Encryption (SSE) with a 256-bit Advanced Encryption Standard (AES) cipher encrypts all data written to Azure Storage.
    
- **Encryption in transit**. Keep your data secure by enabling transport-level security between Azure and the client. 
    
- **Encryption models**. Azure supports various encryption models, including server-side encryption that uses service-managed keys, customer-managed keys in Key Vault, or customer-managed keys on customer-controlled hardware. With client-side encryption, you can manage and store keys on-premises or in another secure location.
    
- **Authorize requests**. For optimal security, Microsoft recommends using Microsoft Entra ID with managed identities to authorize requests against blob, queue, and table data, whenever possible. Authorization with Microsoft Entra ID and managed identities provides superior security and ease of use over Shared Key authorization.
    
- **RBAC**. RBAC ensures that resources in your storage account are accessible only when you want them to be, and to only those users or applications whom you grant access. Assign RBAC roles scoped to an Azure storage account.
    
- **Storage analytics**. Azure Storage Analytics performs logging for a storage account. You can use this data to trace requests, analyze usage trends, and diagnose issues with your storage account.

# Shared Access Signatures
A Shared Access Signature (SAS) is a uniform identifier (URI) that grants restricted access rights to Azure Storage resources.
SAS is a secure way to share your storage resources without compromising your account keys.

You can provide a SAS to clients who shouldnt have access to your storage account key.

# URI
The exmaple creates a service-level SAS that grants read/write permissions to a blob.
```
https://myaccount.blob.core.windows.net/?restype=service&comp=properties&sv=2015-04-05&ss=bf&st=2015-04-29T22%3A18%3A26Z&se=2015-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=F%6GRVAZ5Cdj2Pw4tgU7IlSTkWgn7bUkkAg8P6HESXwmf%4B
```

| Parameter           | Example                                                                                            | Description                                                                                                                                                                                                                                                                                                               |
| ------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Resource URI**    | `https://myaccount.`**`blob`**`.core.windows.net/` `?restype=`**`service`** `&amp;comp=properties` | Defines the Azure Storage endpoint and other parameters. This example defines an endpoint for Blob Storage and indicates that the SAS applies to service-level operations. When the URI is used with `GET`, the Storage properties are retrieved. When the URI is used with `SET`, the Storage properties are configured. |
| **Storage version** | **`sv`**`=2015-04-05`                                                                              | For Azure Storage version 2012-02-12 and later, this parameter indicates the version to use. This example indicates that version 2015-04-05 (April 5, 2015) should be used.                                                                                                                                               |
| **Storage service** | **`ss`**`=bf`                                                                                      | Specifies the Azure Storage to which the SAS applies. This example indicates that the SAS applies to Blob Storage and Azure Files.                                                                                                                                                                                        |
| **Start time**      | **`st`**`=2015-04-29T22%3A18%3A26Z`                                                                | (Optional) Specifies the start time for the SAS in UTC time. This example sets the start time as April 29, 2015 22:18:26 UTC. If you want the SAS to be valid immediately, omit the start time.                                                                                                                           |
| **Expiry time**     | **`se`**`=2015-04-30T02%3A23%3A26Z`                                                                | Specifies the expiration time for the SAS in UTC time. This example sets the expiry time as April 30, 2015 02:23:26 UTC.                                                                                                                                                                                                  |
| **Resource**        | **`sr`**`=b`                                                                                       | Specifies which resources are accessible via the SAS. This example specifies that the accessible resource is in Blob Storage.                                                                                                                                                                                             |
| **Permissions**     | **`sp`**`=rw`                                                                                      | Lists the permissions to grant. This example grants access to read and write operations.                                                                                                                                                                                                                                  |
| **IP range**        | **`sip`**`=168.1.5.60-168.1.5.70`                                                                  | Specifies a range of IP addresses from which a request is accepted. This example defines the IP address range 168.1.5.60 through 168.1.5.70.                                                                                                                                                                              |
| **Protocol**        | **`spr`**`=https`                                                                                  | Specifies the protocols from which Azure Storage accepts the SAS. This example indicates that only requests by using HTTPS are accepted.                                                                                                                                                                                  |
| **Signature**       | **`sig`**`=F%6GRVAZ5Cdj2Pw4tgU7Il` `STkWgn7bUkkAg8P6HESXwmf%4B`                                    | Specifies that access to the resource is authenticated by using a Hash-Based Message Authentication Code (HMAC) signature. The signature is computed with a key using the SHA256 algorithm, and encoded by using Base64 encoding.                                                                                         |
# Storage Encryption
- Protects your data by ensuring your organizational security and compliance commitments are met
- Encryption & decryption process happen automatically
- When you create a storage account Azure generates two 512-bit storage account access keys. Which can be used to authorize access to data.
- Recommended to use Azure Key Value to manage access keys

# Customer-Managed Keys
- By creating your own keys (referred to as _customer-managed_ keys), you have more flexibility and greater control.
    
- You can create, disable, audit, rotate, and define access controls for your encryption keys.
    
- Customer-managed keys can be used with Azure Storage encryption. You can use a new key or an existing key vault and key. The Azure storage account and the key vault must be in the same region, but they can be in different subscriptions.