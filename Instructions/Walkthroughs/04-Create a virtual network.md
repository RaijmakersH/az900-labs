---
wts:
    title: '04 - Create a virtual network (20 min)'
    module: 'Module 02 - Core Azure Services (Workloads)'
---
# 04 - Create a virtual network (20 min)

In this walkthrough, we will create a virtual network, deploy two virtual machines onto that virtual network and then configure them to allow one virtual machine to ping the other within that virtual network.

# Task 1: Create a virtual network 

In this task, we will create a virtual network. 

Note: Before beginning the lab, disable both the public and private firewall in your virtual machine by opening the Start menu > Settings > Network and Internet > Locate Windows Firewall

1. Sign in to the Azure portal at <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. From the **All services** blade, search for and select **Virtual networks**, and then click **+ Add, + Create, + New**. 

3. On the **Basics** tab, fill in the following information (leave the defaults for everything else):

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Leave default provided** |
    | Resource Group | **Create new resource group** |
    | Name | **vnet1** |
    | Region | **(US) East US** |
    
   
4. Click the **Review + create** button. Ensure the validation passes. Then hit create to deploy the resource.


# Task 2: Create two virtual machines

In this task, we will create two virtual machines in the virtual network. 

1. From the **All services** blade, search for **Virtual machines** and then click **+ Add, + Create, + New**, from the drop down select **Virtual Machine**. 

2. On the **Basics** tab, fill in the following information (leave the defaults for everything else):

   | Setting | Value | 
   | --- | --- |
   | Subscription | **Use default supplied** |
   | Resource group |  **Select default in drop down** |
   | Virtual machine name | **vm1**|
   | Region | **(US) East US** |
   | Image | **Windows Server 2019 Datacenter - Gen2** |
   | Username| **azureuser** |
   | Password| **Pa$$w0rd1234** |
   | Public inbound ports| Select **Allow selected ports**  |
   | Selected inbound ports| **RDP (3389)** |
   

3. Select the **Networking** tab. Make sure the virtual machine is placed in the **vnet1** virtual network. Review the default settings, but do not make any other changes. 

4. Click **Review + create**. After the Validation passes, click **Create**. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. Monitor your deployment, but continue on to the next step. 

6. Create a second virtual machine by repeating steps **2 to 4** above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | Setting | Value |
    | --- | --- |
    | Resource group | **select default in dropdown (same as Task1-3 & Task2-2)** |
    | Virtual machine name |  **vm2** |
    | Virtual network | **vnet1** |
    | Public IP | **vm2-ip** |

7. Wait for both virtual machines to deploy and status says *running*.

# Task 3: Test the connection 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the **All resources** blade, search for **vm1**, open its **Overview** blade, and make sure its **Status** is **Running**. You may need to **Refresh** the page.

2. On the **Overview** blade, select **Connect** and then select **RDP** from the drop down.

    **Note**: The following directions tell you how to connect to your VM from a Windows computer. 

3. On the **Connect with RDP** blade, keep the default options to connect by IP address over port 3389 and click **Download RDP File**.

4. Open the downloaded RDP file (located at the bottom left of you VM) and click **Connect** when prompted. 

5. In the **Windows Security** window, type the username **azureuser** and password **Pa$$w0rd1234** and then click **OK**.

6. You may receive a certificate warning during the sign-in process. Click **Yes** to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. In **both** newly created virtual machines, connect via RDP and disable both the public and private firewall by opening the Start menu > Settings > Network and Internet > Locate Windows Firewall.

8. Open up PowerShell on the virtual machine by clicking the **Start** button, and in Search type **PowerShell**, right click on **Windows PowerShell** to **Run as administrator**

9. In Powershell, try to ping vm2 by typing:

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


**Congratulations!** You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

**Note**: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.
