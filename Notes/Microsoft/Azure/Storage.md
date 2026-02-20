Azure storage has 3 categories of data:

|Category|Description|Storage examples|
|---|---|---|
|**Virtual machine data**|Virtual machine data storage includes disks and files. Disks are persistent block storage for Azure IaaS virtual machines. Files are fully managed file shares in the cloud.|Storage for virtual machine data is provided through Azure managed disks. Data disks are used by virtual machines to store data like database files, website static content, or custom application code. The number of data disks you can add depends on the virtual machine size.|
|**Unstructured data**|Unstructured data is the least organized. The format of unstructured data is referred to as _nonrelational_.|Unstructured data can be stored by using Azure Blob Storage and Azure Data Lake Storage. Blob Storage is a highly scalable, REST-based cloud object store. Azure Data Lake Storage is the Hadoop Distributed File System (HDFS) as a service.|
|**Structured data**|Structured data is stored in a relational format that has a shared schema. Structured data is often contained in a database table with rows, columns, and keys. Tables are an autoscaling NoSQL store.|Structured data can be stored by using Azure Table Storage, Azure Cosmos DB, and Azure SQL Database. Azure Cosmos DB is a globally distributed database service. Azure SQL Database is a fully managed database-as-a-service built on SQL.|
# Storage Services
## Blob Storage
A service that stores unstructured data in the cloud as objects or Blobs.
Blob -> Binary Large Object

![](/Images/blob_azure.png)

Blob Storage is optimized for storing massive amounts of unstructured or non-relational data. It is ideal for:
- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming video and audio.
- Storing data for backup and restore, disaster recovery, and archiving.
- Storing data for analysis by an on-premises or Azure-hosted service.

- Can store any type of text or binary data
- Uses 3 resources to store and manage your data:
	- Azure storage account
	- Containers
	- Blobs in containers
- All blobs must be in a container
- Containers organize blob storage
- Containers and store an unlimited amount of blobs
- Must create a storage container before you can begin to upload data
### Access Tiers
**Hot** - Optimized for frequent read/write of objects
**Cool** - Optimized for storing large amount of infrequently accessed data
**Cold** - Same as cool but for data that can remain in the tier for at least 90 days
**Archive** - Offline tier optimized for data that can tolerate several hours of retrieve latency

**You can create rules to alter blobs**

| Comparison                       | Hot access tier | Cool access tier | Cold access tier | Archive access tier |
| -------------------------------- | --------------- | ---------------- | ---------------- | ------------------- |
| **Availability**                 | 99.9%           | 99%              | 99%              | 99%                 |
| **Availability (RA-GRS reads)**  | 99.99%          | 99.9%            | 99.9%            | 99.9%               |
| **Latency (time to first byte)** | milliseconds    | milliseconds     | milliseconds     | hours               |
| **Minimum storage duration**     | N/A             | 30 days          | 90 days          | 180 days            |
### Object Replication
Copies blobs in a container asynchronously according to policy rules that you can configure.
![](/Images/object_repliaction_blob_azure.png)

- Required blob versioning enabled on both source and destination accounts
- Doesn't support blob snapshots
- Accounts need to be in Host, Cool or Cold teir
### Manage Blobs
There are 3 types of blobs:
- Black blobs - Blocks of data assembled to make a blob
- Append blobs - Same as black blob but optimized for append operations
- Page blobs - Can be up to 8TB, efficient for read/write

You can use the portal to upload/manage blobs. If your using a large number of files use a tools such as:
1. Azure Storage Explorer
2. AzCopy
3. Azure Data Box Disk

## Files
Lets you setup a highly available network file shares.
Can be accessed using SMB protocol and NFS protocol.
Some example scenarios where file shares can be used:
- Many on-premises applications use file shares. This feature makes it easier to migrate those applications that share data to Azure. If you mount the file share to the same drive letter that the on-premises application uses, the part of your application that accesses the file share should work with minimal, if any, changes.
- Configuration files can be stored on a file share and accessed from multiple virtual machines. Tools and utilities used by multiple developers in a group can be stored on a file share, ensuring that everybody can find them, and that they use the same version.
- Diagnostic logs, metrics, and crash dumps are just three examples of data that can be written to a file share and processed or analyzed later.
## Queue Storage
Used to store and retrieve messages.
Messages can be up to 64KB in size.
## Table Storage
A service that stores non-relational structured data in the cloud.
Is easy to adapt your data as the needs of your application evolve.

# Storage Account Types
| Storage account                                                                                                       | Supported services                                                                        | Recommended usage                                                                                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**Standard** **general-purpose v2**](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-upgrade) | Blob Storage (including Data Lake Storage), Queue Storage, Table Storage, and Azure Files | Standard storage account for most scenarios, including blobs, file shares, queues, tables, and disks (page blobs).                                                                                                                                                                  |
| [**Premium** **block blobs**](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-block-blob-premium)  | Blob Storage (including Data Lake Storage)                                                | Premium storage account for block blobs and append blobs. Recommended for applications with high transaction rates. Use Premium block blobs if you work with smaller objects or require consistently low storage latency. This storage is designed to scale with your applications. |
| [**Premium** **file shares**](https://learn.microsoft.com/en-us/azure/storage/files/storage-how-to-create-file-share) | Azure Files                                                                               | Premium storage account for file shares only. Recommended for enterprise or high-performance scale applications. Use Premium file shares if you require support for both Server Message Block (SMB) and NFS file shares.                                                            |
| [**Premium** **page blobs**](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-pageblob-overview)    | Page blobs only                                                                           | Premium high-performance storage account for page blobs only. Page blobs are ideal for storing index-based and sparse data structures, such as operating systems, data disks for virtual machines, and databases.                                                                   |

# Replication Stategies
Your data is always replicated to ensure durability and high availability.

## Locally Redundant Storage
![](/Images/locall_redundant_storage_azure.png)
- Lowest-cost
- Least durable
## Zone Redundant Storage
![](/Images/zone_redundant_storage_azure.png)
- Replicates your data across 3 storage clusters in a single region
- Each storage cluster is physically separated from each other
- Is not available in all regions
## Geo-Redundant Storage
![](/Images/geo-redundant_storage_azure.png)
- Replicated your data to a secondary region
- Provides high durability
# Geo-Zone Redundant Storage
![](/Images/geo-zone_redundant_storage_azure.png)
- Protection from regional outages
- Storage account is replicated across 3 zones in primary region
# Access Storage
Every object stored in Azure Storage has a unique URL address.
Some examples:

|Service|Default endpoint|
|---|---|
|**Container service**|`//`**`mystorageaccount`**`.blob.core.windows.net`|
|**Table service**|`//`**`mystorageaccount`**`.table.core.windows.net`|
|**Queue service**|`//`**`mystorageaccount`**`.queue.core.windows.net`|
|**File service**|`//`**`mystorageaccount`**`.file.core.windows.net`|
  