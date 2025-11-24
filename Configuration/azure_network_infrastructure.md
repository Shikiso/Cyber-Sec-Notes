# Create a Resource Group
1. Search for **Resource Groups** and click **Resource groups**

![](/Images/azure_resource_group_1.png)

2. Click **Create**

![](/Images/azure_resource_group_2.png)

3. Select your subscription, name and region
4. Click **Review + Create** then **Create**
# Create a Virtual Networks
1. Search for and select **Virtual Networks**

![](/Images/azure_virtual_network_1.png)

2. Click **Create**
3. Fill in the **Subscription**, **Resource Group**, **Virtual Network name** and **region**.
4. Click **Next** until **IP addresses**
5. Fill in your address prefix for example **10.0.0.0/16**
## Add Subnets
1. (Either delete the existing subnet or edit it, ill be editing it)
2. On the **IP addresses** page click the pencil icon on the **default** subnet

![](/Images/azure_virtual_network_3.png)

3. Change the **Name** and set the addressing to your needs

![](/Images/azure_virtual_network_4.png)

4. Click **Save**
5. To add another subnet click **Add a subnet**

![](/Images/azure_virtual_network_2.png)

6. And the same process applies, add a **Name** and fill in the networking information to your needs

![](/Images/azure_virtual_network_5.png)

7. Click **Add**
8. Click **Review + create** then **Create**
# Create a Public IP Address
1. Search and select **Public IP addresses**

![](/Images/azure_public_ip_1.png)

2. Click **Create**
3. Enter the **Resource Group**, **Name** and **Region**, I will be using a static **Allocation Method**

![](/Images/azure_public_ip_2.png)

4. Click **Review + create** then **Create**
# Create a Network Security Group
1. Search and select **Network security groups**

![](/Images/azure_network_interface_1.png)

2. Click **Create**
3. Enter your **Resource group**, **Name** and **Region**
4. Click **Review + create** then **Create**
## Adding Rules
1. Click **Go to resource**
2. Open the **Setting** band and select either **Inbound security rules** or **Outbound security rules**

![](/Images/azure_network_interface_2.png)

3. Click **Add**
4. Fill in the properties of the rule you want to create

![](/Images/azure_network_interface_3.png)

5. Click **Add**
## Add Network Security Group to subnets

1. Open the **Setting** band and click **Subnets**
![](/Images/azure_network_interface_4.png)

2. Click **Associate**
3. Select your **Virtual network** and **Subnet**
4. Click **OK**
# Create NIC
1. Search and select **Network Interface**
2. Enter your **Resource Group**, **Name**, **Region**, **Virtual Network** and **Subnet**
3. Click **Review + create** then **Create**
## Add Public IP to NIC
1. Go to resource
2. Open the **Settings** band and click **IP configuration**

![](/Images/azure_network_interface_5.png)

2. Click on the config
![](/Images/azure_network_interface_6.png)

4. Check **Associate public IP address**
5. Select your **Public IP** and click **Save**
(Go to **Overview** to check if public IP has been added)

![](/Images/azure_network_interface_7.png)
# Create VM
1. Search and select **Virtual machines**

![](/Images/azure_vm_1.png)

2. Click **Create** and select **Virtual machine**

![](/Images/azure_vm_2.png)

3. Set the **Virtual machine name**, **Region**, **Username** and **Password**

![](/Images/azure_vm_3.png)

4. Press **Next** and select a appropriate disk size
5. Press **Next**
6. Select your **Virtual Network**, **Public IP** and **Subnet**

![](/Images/azure_vm_4.png)

7. Click **Review and create** then click **Create**
## Add NIC
1. Go to resource
2. Stop the VM from running

![](/Images/azure_vm_6.png)

3. Open the **Networking** blade and click **Network Settings**
4. Click **Attach network interface**

![](/Images/azure_vm_5.png)

5. Select the NIC and click **OK**
(Can't add more due to administrator limitations)