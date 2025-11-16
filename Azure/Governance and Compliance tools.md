# Microsoft Purview
Is a family of data governance, risk and compliance solutions that helps you get a single unified view into your data.
## Risk and Compliance Solutions
Purview uses these tools to help manage/monitor your data:
- Microsoft Teams
- OneDrive
- Exchange

Purview has data governance solutions which enable you to manage your data stored in Azure, SQL and Hive databases.

# Azure Policy
Lets you create, assign and manage policies that control or audit your resources.

Azure lets you define both individual policies and group related policies (known as initiatives).

Azure policies are inherited, meaning a policy placed high up will be applied to all grouping with the parent.

## Initiatives
A way of grouping related policies together.
The initiative definition contains all of the policy definitions to help track your compliance state for a larger goal.

# Resource Locks
Prevents resources from being deleted or changed.
## Types
There are two types of resource locks:
- Delete means authorized users can still read and modify a resource, but they can't delete the resource.
- ReadOnly means authorized users can read a resource, but they can't delete or update the resource. Applying this lock is similar to restricting all authorized users to the permissions granted by the Reader role.
## Alter a locked resource
To modify a locked resource you must remote the lock.

# Service Trust Portal
Provides access to various content, tools and other resources about Microsoft security, privacy and compliance practices.