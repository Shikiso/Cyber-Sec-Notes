All users who need access to Azure resources need an Azure user account.
Once authenticated Entra ID creates an access token to authorize the user and determine what resources they can access.
# Users
Users are located under identity, you can open All users to view (take a guess) all users.

Users are defines in 3 ways:
- Cloud Identities - Only exist in Entra ID. Admins and self managed users
- Directory-synchronized identities - Created in an on-premises AD then synchronized to Entra ID
- Guess - Users outside Azure

## Create new User
- Browse to the Identity menu in the [Microsoft Entra admin center](https://entra.microsoft.com/).
- In the left navigation, under select **Users**, then **All Users.**
- Within the Users page, on the menu, select + **New user** and **Create new user**.

## Create security Group
- Browse to the Microsoft Entra admin center screen.
- In the left navigation, under **Identity**, select **Groups** and then **All groups**.
- In the Groups screen, on the menu, select **New group**.
- Create a group using the following information:
## Assign license to Group
1. In the **All groups** list, select **Marketing**.
2. In the Marketing window, under **Manage**, select **Licenses**.
3. Notices that no licenses are currently assigned to this group.
4. Open a new tab in your browser.
5. Go to the Microsoft 365 admin center at [http://admin.microsoft.com](https://admin.microsoft.com).
6. Select **Billing** from the menu on the left.
7. Select **Licenses**.
8. From the list of licenses you have available, select one.
9. Next you select **Groups** from the list near the top of the screen.  
10. On the Groups page, select + **Assign license**.  
11. Search for and select the **Marketing** group we created earlier.
12. Select the **Assign** button at the bottom of the dialog.
13. You should get a message that licenses were successfully assigned.
## Remove User
- Browse to the [Microsoft Entra admin center](https://entra.microsoft.com/).
- In the left navigation, under **Identity**, select **Users**.
- In the **Users** list, select the check box for a user to delete.
- With the user account selected, on the menu, select **Delete user**.
## Restore a deleted User
(By default, deleted user accounts are permanently removed from Microsoft Entra ID automatically after 30 days.)
1. In the Users page, in the left navigation, select **Deleted users**.
2. Review the list of deleted users and select the user you deleted.
3. On the menu, select **Restore user**.
4. Review the dialog box and then select **OK**.
5. In the left navigation, select **All users**.

# Groups
There are two types of groups:
- Security groups - Used to manage member and computer access to shared resources.
- Microsoft 365 groups - Provides collaboration opportunities (gives members access to shared resources.)

Groups can be assigned and maintained manually or dynamically.

# Device Registration
Used to provide users support for BYOD or mobile device scenarios.

|**Microsoft Entra registered**|**Description**|
|---|---|
|Definition|Registered to Microsoft Entra ID without requiring organizational account to sign in to the device|
|Primary audience|Applicable to Bring your own device (BYOD), and Mobile devices|
|Device ownership|User or Organization|
|Operating systems|Windows 10, Windows 11, iOS, Android, and macOS|
|Device sign in options|End-user local credentials, Password, Windows Hello, PIN Biometrics|
|Device management|Mobile Device Management (example: Microsoft Intune)|
|Key capabilities|SSO to cloud resources, Conditional Access|
## Entra Joined Devices
Intended for organizations that want to be cloud first or cloud only.
Enables access to both cloud and on-premises apps and resources.

|**Microsoft Entra joined**|**Description**|
|---|---|
|Definition|Joined only to Microsoft Entra ID requiring organizational account to sign in to the device|
|Primary audience|Suitable for both cloud-only and hybrid organizations|
|Device ownership|Organization|
|Operating systems|All Windows 10 & 11 devices except Windows 10/11 Home|
|Device management|Mobile Device Management (example: Microsoft Intune)|
|Key capabilities|SSO to both cloud and on-premises resources, Conditional Access, Self-service Password Reset and Windows Hello PIN reset|
Access to resources can be limited based on the Entra account and Condition Access policies applied to the device identity.
Further control can be implemented using Mobile Device Management (MDM) tools.

### Hybrid
Used for when environment has on-premises AD footprint and you want capabilities provides by Entra ID.

|**Hybrid Microsoft Entra joined**|**Description**|
|---|---|
|Definition|Joined to on-premises AD and Microsoft Entra ID requiring organizational account to sign in to the device|
|Primary audience|Suitable for hybrid organizations with existing on-premises AD infrastructure|
|Device ownership|Organization|
|Operating systems|Windows 11, 10, 8.1 and 7, along with Windows Server 2008/R2, 2012/R2, 2016 and 2019|
|Device sign in options|Password or Windows Hello for Business|
|Device management|Group Policy, Configuration Manager standalone or co-management with Microsoft Intune|
|Key capabilities|SSO to both cloud and on-premises resources, Conditional Access, Self-service Password Reset and Windows Hello PIN reset|