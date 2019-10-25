In this walkthrough, we will create a virtual machine in the Azure Portal, connect to the virtual machine, install the web server role and test. 

Estimated time: 45 minutes

**Note**: Take time during this walk-through to click and read the Informational icons. 

**Task 1: Create the virtual machine**

In this task, we will create a Windows Server 2016 Datacenter virtual machine. 

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Search for **Virtual machines** and then click **+Add**.

3. In the **Basics** tab, fill in the information. Leave the defaults for everthing else.

    | Settings | Values |
    |--|--|
    | Subscription | **Choose your subscription**|
    | Resource group | **myRGVM** (create new) |
    | Virtual machine name | **myVm** |
    | Location | **(US) East US**|
    | Image | **Windows Server 2016 Datacenter**|
    | Administrator account username | **azureuser** |
    | Administrator account password | **Pa$$w0rd1234**|
    | Inbound port rules - Allow select ports | **RDP (3389)** and **HTTP (80)**|

4. Move to the Management tab and the **Monitoring** section.

    | Settings | Values |
    |--|--|
    | Boot diagnostics | **Off**|

5. Leave the remaining defaults and then select the **Review + create** button at the bottom of the page.

6. Once Validation is passed click the **Create** button. It can take anywhere from five to seven minutes to deploy the virtual machine.

7. You will receive updates on the deployment page and on the **Notifications** icon (top menu).

**Task 2: Connect to the virtual machine**

In this task, we will connect to our new virtual machine using RDP. 

1. Search for **myVM** and select your new virtual machine.

**Note**: You could also use the **Go to resource** link in the **Notifications**. 

2. On the virtual machine **Overview** page, click the **Connect** button.

    ![Screenshot of the virtual machine properties with the Connect button highlighted.](../../Linked_Image_Files/walkthrough-createvmportal6.png)

    **Note**: The following directions tell you how to connect to your VM from a Windows computer. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store and on Linux virtual machine you could connect directly from a bash shell using `ssh`.

2. In the **Connect to virtual machine** page, keep the default options to connect with the public IP address over port 3389 and click **Download RDP File**.

3. **Open** the downloaded RDP file and click **Connect** when prompted. 

    ![Screenshot of the virtual machine properties with the Connect button highlighted. ](../../Linked_Image_Files/walkthrough-createvmportal8.png)

4. In the **Windows Security** window, select **More choices** and then **Use a different account**. Provide the username (.\azureuser) and the password (Pa$$w0rd1234). Click **OK** to connect.

    ![Screenshot of the Windows security dialogue with use a different account selected and the username azure user entered and a password.](../../Linked_Image_Files/walkthrough-createvmportal9.png)


5. You may receive a certificate warning during the sign-in process. Click **Yes** or to create the connection and connect to your deployed VM. You should connect successfully.

    ![Screenshot of the Certificate warning dialogue informing the user of an untrusted certificate, with the Yes button highlighted. ](../../Linked_Image_Files/walkthrough-createvmportal10.png)

Congratulations! You have deployed and connected to a Windows Server virtual machine in Azure

**Task 3: Install the web server role and test**

In this task, install the Web Server role on the server and ensure the default IIS welcome page can be displayed.

1. Open up a PowerShell command prompt on the virtual machine, by clicking the **Start** button, typing **PowerShell** right clicking **Windows PowerShell** in the menu and selecting **Run as administrator**

    ![Screenshot of the virtual machine desktop with the start button clicked and PowerShell selected with run as an administrator highlighted.](../../Linked_Image_Files/walkthrough-createvmportal11.png)

2. Install the **Web-Server** feature in the virtual machine by running the following command in the PowerShell command prompt. You can copy and paste this command.

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. When completed there will be a prompt stating **Success** with a value **True**. You do not need to restart the virtual machine to complete the installation. Close the RDP connection to the VM.

    ![Screenshot of the windows PowerShell command prompt with the command Install-WindowsFeature -name Web-Server -IncludeManagementTools successfully completed and output stating it was successful.](../../Linked_Image_Files/walkthrough-createvmportal13.png)

4. Back in the portal, select the VM and in the **Overview** pane of the VM, use the **Click to copy** button to the right of the public IP address to copy it and paste it into a browser tab.

    ![Screenshot of the Azure portal virtual machine property pane with the IP address copied.](../../Linked_Image_Files/walkthrough-createvmportal14.png)

5. The default IIS Web Server welcome page will open, and is available to connect to publicly via this IP address, or via the fully qualified domain name.

    ![Screenshot of the default IIS web server welcome page being accessed via the public ip address in a web browser.](../../Linked_Image_Files/walkthrough-createvmportal15.png)

Congratulations! You have created a web server that can be connected to publicly via this IP address, or via the fully qualified domain name. If you had a web page to host you could deploy those source files to the virtual machine and host them for public access on the deployed virtual machine.


**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.