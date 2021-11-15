---
wts:
    title: '10 - Create a VM with PowerShell (10 min)'
    module: 'Module 03: Describe core solutions and management tools'
---
# 10 - Create a VM with PowerShell (10 min)

In this walk-through, we will configure the Cloud Shell, use Azure PowerShell module to create a resource group and virtual machine, and review Azure Advisor recommendations. 

# Task 1: Configure the Cloud Shell 

In this task, we will configure Cloud Shell. 

1. Sign in to the [Azure portal](https://portal.azure.com).** You can find your login credentials within the resources tab (directly next to this Instructions tab!)
**
2. From the Azure portal, open the **Azure Cloud Shell** by clicking on the icon in the top right of the Azure Portal.

    ![Screenshot of Azure Portal Azure Cloud Shell icon.](../images/1002.png)

3. When prompted to select either **Bash** or **PowerShell**, select **PowerShell**.

4. On the **You have no storage mounted** screen select **Show advanced settings** then fill in the information below

    | Settings | Values |
    |  -- | -- |
    | Resource Group | **Create new resource group** |
    | Storage account (Create a new account a use a globally unique name (ex: cloudshellstoragemystorage)) | **cloudshellxxxxxxx** |
    | File share (create new) | **shellstorage** |

5. Select **Create Storage**

# Task 2: Create a resource group and virtual machine

In this task, we will use PowerShell to create a resource group and a virtual machine.  

1. Ensure **PowerShell** is selected in the upper-left drop-down menu of the Cloud Shell pane.

2. Verify your new resource group by running the following command in the Powershell window. Press **Enter** to run the command.

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. Create a virtual machine by pasting the following command into the terminal window. 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. When prompted provide the username (**azureuser**) and the password (**Pa$$w0rd1234**) that will be configured as the local Administrator account on that virtual machines.azureadmin

5. Once VM is created, close the PowerShell session Cloud Shell pane.

6. In the Azure portal, search for **Virtual machines** and verify the **myVMPS** is running. This may take a few minutes.

    ![Screenshot of the virtual machines page with myVMPS in a running state.](../images/1001.png)

7. Access the new virtual machine and review the Overview and Networking settings to verify your information was correctly deployed. 

# Task 3: Execute commands in the Cloud Shell

In this task, we will practice executing PowerShell commands from the Cloud Shell. 

1. From the Azure portal, open the **Azure Cloud Shell** by clicking on the icon in the top right of the Azure Portal.

2. Ensure **PowerShell** is selected in the upper-left drop-down menu of the Cloud Shell pane.

3. Retrieve information about your virtual machine including name, resource group, location, and status. Notice the PowerState is **running**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Stop the virtual machine using the following command. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. When prompted confirm (Yes) to the action. Wait for **Succeeded** status.

6. Verify your virtual machine state. The PowerState should now be **deallocated**. You can also verify the virtual machine status in the portal. Close Cloudshell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# Task 4: Review Azure Advisor Recommendations

**Note:** This same task is in the Create a VM with Azure CLI lab. 

In this task, we will review Azure Advisor recommendations for our virtual machine. 

1. From the **All services** blade, search for and select **Advisor**. 

2. On the **Advisor** blade, select **Overview**. Notice recommendations are grouped by Reliability, Security, Performance, and Cost. 

    ![Screenshot of the Advisor Overview page. ](../images/1003.png)

3. Select **All recommendations** and take time to view each recommendation and suggested actions. 

    **Note:** Depending on your resources, your recommendations will be different. 

    ![Screenshot of the Advisor All recommendations page. ](../images/1004.png)

4. Notice that you can download the recommendations as a CSV or PDF file. 

5. Notice that you can create alerts. 

6. If you have time, continue to experiment with Azure PowerShell. 

Congratulations! You have configured Cloud Shell, created a virtual machine using PowerShell, practiced with PowerShell commands, and viewed Advisor recommendations.

**Note**: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.
