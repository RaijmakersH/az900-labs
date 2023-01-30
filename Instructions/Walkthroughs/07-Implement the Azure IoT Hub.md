---
wts:
    title: '07 - Implement an Azure IoT Hub (10 min)'
    module: 'Module 03: Describe core solutions and management tools'
---
# 07 - Implement an Azure IoT Hub (10 min)

In this walkthrough, we will configure a new Azure IoT Hub in Azure Portal, and then authenticate a connection to an IoT device using the online Raspberry Pi device simulator. Sensor data and messages are passed from the Raspberry Pi simulator to your Azure IoT Hub, and you view metrics for the messaging activity in Azure Portal.

# Task 1: Create an IoT hub 

In this task, we will create an IoT hub. 

1. Sign in to the [Azure portal](https://portal.azure.com).

2. From the **All services** blade, search for and select **IoT Hub** and then click **+ Add, + Create, + New**.

3. On the **Basics** tab of the **IoT hub** blade, fill in the fields with the following details (replace **xxxx** in the name of the storage account with letters and digits such that the name is globally unique):

    | Settings | Value |
    |--|--|
    | Subscription | **Keep default supplied** |
    | Resource Group | **Create new resource group** |
    | IoT Hub Name | **my-hub-groupxxxxx** |
    | Region | **East US** |
    | Pricing | **Standard** |

    **Note** - Remember to change the **xxxxx** so that it makes a unique **IoT Hub Name**.

4. Click the **Review + create** button.

5. Click the **Create** button to begin creating your new Azure IoT Hub instance.

6. Wait until the Azure IoT Hub instance is deployed. 

# Task 2: Add an IoT device

In this task, we will add an IoT device to the IoT hub. 

1. When the deployment has completed, click **Go to resource** from the deployment blade. Alternatively, from the **All services** blade, search for and select **IoT Hub** and locate your new IoT Hub instance

	![Screenshot of the deployment in progress and deployment succeeded notifications in Azure portal.](../images/0601.png)

2. To add a new IoT device, scroll down to the **Device management** section and click **Devices**. Then, click **+ Add Device**.

	![Screenshot of the IoT devices pane, highlighted within the IoT hub navigation blade, in Azure portal. The New button is highlighted to illustrate how to add a new IoT device identity to IoT hub.](../images/0602.png)

3. Provide a name for your new IoT device, **myRaspberryPi**, and click the **Save** button. This will create a new IoT device identity in your Azure IoT Hub.

4. If you do not see your new device, **Refresh** the IoT Devices page. 

5. Select **myRaspberryPi** and copy the **Primary Connection String** value. You will use this key in the next task to authenticate a connection to the Raspberry Pi simulator.

	![Screenshot of the Primary Connection String page with the copy icon highlighted.](../images/0603.png)

# Task 3: Test the device using a Raspberry Pi Simulator

In this task, we will test our device using the Raspberry Pi Simulator. 

1. Open a new tab in the web browser and type this shortcut link https://aka.ms/RaspPi. It will take you to a Raspberry Pi Simulator site. If you have time, read about the Raspberry Pi simulator. When done select "**X**" to close the pop-up window.

2. In the code area on the right side, locate the line with 'const connectionString ='. Replace it with the connection string you copied from the Azure portal. Note that the connection sting includes the DeviceId (**myRaspberryPi**) and SharedAccessKey entries.

	![Screenshot of the coding area within the Raspberry Pi simulator.](../images/0604.png)

3. Click **Run** (below the code area) to run the application. The console output should show the sensor data and messages that are sent from the Raspberry Pi simulator to your Azure IoT Hub. Data and messages are sent each time the Raspberry Pi simulator LED flashes. 

	![Screenshot of the Raspberry Pi simulator console.  The console output shows sensor data and messages sent from the Raspberry Pi simulator to Azure IoT Hub.](../images/0605.png)

5. Click **Stop** to stop sending data.

6. Return to the Azure portal.

7. Switch the IoT Hub **Overview** blade and scroll down to the **IoT Hub Usage** information to view usage. Change your timeframe in the **show data for last** to see data in the last hour.

	![Screenshot of metrics within the IoT hub usage area of Azure portal.](../images/0606.png)


Congratulations! You have set up Azure IoT Hub to collect sensor data from an IoT device.

**Note**: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.
