# Installing roles and Features
1. Click **Manage** > **Add Roles and Features**

![](/Images/ADDS_config_help_1.png)

2. Press **Next** until you reach the **Server Roles** page
3. Select the role you want to install and click **Add Feature** (You can install multiple at once)
![](/Images/ADDS_config_help_2.png)
4. Click **Next**
5. Select the feature you want to install and click **Add Feature** (You can install multiple at once)
6. Click **Next** until you reach the **Confirmation** page and click **Install**
7. Once installation has finished check for a alert on the flag icon and if necessary complete what it is asking. Examples below.
## AD DS
![](/Images/ADDS_config_help_3.png)

**(Select the deployment operation that applies)**

![](/Images/ADDS_config_help_4.png)
![](/Images/ADDS_config_help_5.png)
![](/Images/ADDS_config_help_6.png)
![](/Images/ADDS_config_help_7.png)
![](/Images/ADDS_config_help_8.png)
![](/Images/ADDS_config_help_9.png)
# Create a new Organizational Unit
1. **Tools** > **Active Directory Users and Computers**
![](/Images/ADDS_config_help_10.png)
2. Right click the domain > **New** > **Organizational Unit**
![](/Images/ADDS_config_help_12.png)
3. Enter a name and press **OK**

![](/Images/ADDS_config_help_13.png)
# Create a new Group
**(You can create a group inside a domain or OU)**
1. Right click the location you want to make a new group (in this case an OU)
2. Click **New** > **Group**

![](/Images/ADDS_config_help_14.png)

3. Set the **Group Name**, **Scope** and **Type** (I left scope and type as default)

![](/Images/ADDS_config_help_15.png)

4. Press **OK**
# Create a new User
1. Open **Active Directory Users and Computers**
![](/Images/ADDS_config_help_16.png)

2. Right click **Users** > **Add** > **New User**

![](/Images/ADDS_config_help_17.png)

3. Fill in the user information and press **Next**

![](/Images/ADDS_config_help_18.png)

4. Set a password and press **Next**

![](/Images/ADDS_config_help_19.png)
# Adding User to a Group
1. Click on the **OU** and double click on the **Group** (In the screenshot both names Training)
![](/Images/ADDS_config_help_20.png)

2. Select **Members** than **Add**

![](/Images/ADDS_config_help_21.png)

3. Enter the Users name and click **Check Names**

![](/Images/ADDS_config_help_22.png)

4. The name will change then click **OK** then **Apply** and **OK**

![](/Images/ADDS_config_help_23.png)
# Group Policy
1. **Tools** > **Group Policy Management**

![](/Images/ADDS_config_help_24.png)

2. Create Group Policy Objects and link them to the OUs or Groups
3. To link a GPO to an OU  right click the OU
4. Click Link an Existing GPO

![](/Images/ADDS_config_help_25.png)

5. Click the GPO and press **OK**

![](/Images/ADDS_config_help_26.png)
# Create backups
1. **Tools** > **Windows Server Backup**

![](/Images/ADDS_config_help_27.png)

2. Right click **Local Backup** > **Backup Schedule**

![](/Images/ADDS_config_help_28.png)

3. Select either **Full Server** or **Custom** if you want to backup a specific drive then click **Next**

![](/Images/ADDS_config_help_29.png)

4. Click **Add Items** and specific what you want to backup by checking the box next to it

![](/Images/ADDS_config_help_30.png)

5. Click **Next**
6. Set the time and how often you want to backup

![](/Images/ADDS_config_help_31.png)

7. Click **Next**
8. Select where to backup, I used **Backup to hard disk**
9. Confirm and finish
# Reliability Monitor
**Control Pane**l > **System and Security**> **Security and Maintenance** > **Maintenance** > **View Reliability History**
# Create a Data Collector Set
1. Open **Performance Monitor** in start menu
2. **Data Collector Sets** > **User Defined**
3. Right click **User Defined**
4. **New** > **Data Collector Set**
5. Enter a name
6. Select **System Performance**
7. Click **Finish**
8. Right click on the collector set and click **start**
9. Wait 60s
10. Right click on the collector set and click **stop**
11. Right click on the collector set and click **Latest Report**
# Restore Local Data
(Can't show how to do this since I only have 1 drive)
1. Open **Windows Server Backup**
2. Select Recover

![](/Images/ADDS_config_help_32.png)

3. Follow the wizard
