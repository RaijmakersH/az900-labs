---
wts:
    title: '11 - Create a VM with the CLI'
    module: 'Module 02 - Core Azure Services'
---


In this walkthrough, we will install the Azure CLI locally, create a resource group and virtual machine, use the Cloud Shell, and review Azure Advisor recommendations. 

Estimated time: 35 minutes

**Note**: The following steps are based on a Windows installation, however they could equally be applicable to a Mac or Linux environment. However, there are [specific installation steps for each environment](https://docs.microsoft.com/cli/azure/install-azure-cli).

**Task 1: Install the CLI locally**

In this task, we will install the Azure CLI on your local machine. 

1. Download the [Azure CLI msi](https://aka.ms/installazurecliwindows) and in the browser, select **Run**. It will take a minute for the files to download.

2. In the Microsoft Azure CLI Setup wizard, click the box **I accept the terms in the license agreement** and then click **Install**.

3. In the **User Account Control** dialog, select **Yes** to indicate the app can make changes to your device. 

4. Once the installation is complete select **Finish**.

    **Note:** The Azure CLI is run by opening a Bash shell in the Linux or macOS, or it can be run from the command prompt or PowerShell app in Windows. 

**Task 2: Create a resource group and a virtual machine**

1. On your local machine, open a **Command Prompt**. Be sure to **Run as administrator**. If prompted, confirm (Yes) the app can make changes to your device.

    **Note**: You can run the Azure CLI from a PowerShell session rather than from the Windows Command Prompt. Running the CLI from PowerShell has some advantages such as more tab completion features.

2. Login to your Azure subscription. Select the account associated with your subscription and wait to be successfully logged in. 

    ```azurecli
    az login
    ```

3. If you like, bookmark the [Azure CLI Documentation](https://docs.microsoft.com/en-us/cli/azure/?view=azure-cli-latest) page.

4. Verify your installation by running the version check command and ensuring it runs successfully. A warning message about being unable to check for the latest updates, is okay. 

    ```cli
    az --version
    ```

5. Create a new resource group.

    ```cli
    az group create --name myRGCLI --location EastUS
    ```

6. Verify the resource group was created.

    ```cli
    az group list --output table
    ```

6. Create a new virtual machine. This command must all be on one line. And, there should not be any tick (`) marks when it is all on one line. 


    ```cli
    az vm create `
        --name myVMCLI `
        --resource-group myRGCLI `
        --image UbuntuLTS `
        --location EastUS `
        --admin-username azureuser `
        --admin-password Pa$$w0rd1234
    ```

    **Note**: The command will take 2 to 3 minutes to complete. The command will create a virtual machine and various resources associated with it such as storage, networking and security resources. Do not continue to the next step until the virtual machine deployment is complete. You can close the Azure Cloud Shell once it is complete.


5. When the command finishes running, sign in to the [Azure portal](https://portal.azure.com).

6. Search for **Virtual machines** and verify that **myVMCLI** is running.

    ![Screenshot of the virtual machines page with myVMPS in a running state.](../images/1101.png)

7. Close your local CLI session. 

**Task 3: Execute commmands in the Cloud Shell**

In this task, we will practice executing CLI commands from the Cloud Shell. 

1. From the portal, open the **Azure Cloud Shell** by clicking on the *Azure Cloud Shell icon* in the top right of the Azure Portal.

    ![Screenshot of Azure Portal Azure Cloud Shell icon.](../images/1102.png)

2. If you have previously used the Cloud Shell skip ahead to Step 5. 

3. When prompted to select either **Bash** or **PowerShell**, select **Bash**. 

4. When prompted, **Create storage**, and allow the Azure Cloud Shell to initialize. 

5. Ensure **Bash** is selected in the upper-left drop-down menu.

**Notice you will not need to login when using the shell.**

6. Retrieve information about your virtual machine including name, resource group, location, and status. Notice the PowerState is **running**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

7. Stop the virtual machine. Notice the message that billing continues until the virtual machine is deallocated. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

8. Verify your virtual machine status. The PowerState should now be **stopped**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

**Task 4: Review Azure Advisor Recommendations**

**Note:** This same task is in the Create a VM with Azure PowerShell walkthrough. 

In this task, we will review Azure Advisor recommendations. 

    **Note:** If you have done the previous lab (Create a VM with PowerShell) then you have already completed this task. 

1. From the portal, search for and select **Advisor**. 

2. In Advisor, select **Overview**. Notice recommendations are grouped by High Availability, Security, Performance, and Cost. 

    ![Screenshot of the Advisor Overview page. ](../images/1103.png)

3. Select **All recommendations** and take time to view each recommendation and suggested actions. 

    **Note:** Depending on your resources, your recommendations will be different. 

    ![Screenshot of the Advisor All recommendations page. ](../images/1104.png)

4. Notice that you can download the recommendations as a CSV or PDF file. 

5. Notice that you can create alerts. 

6. As you have time, continue to experiment with the Azure CLI.

Congratulations! You have installed PowerShell on your local machine, created a virtual machine using PowerShell, practiced with PowerShell commands, and viewed Advisor recommendations.

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.

