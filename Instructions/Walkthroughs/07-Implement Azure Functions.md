---
wts:
    title: '07 - Implement Azure Functions'
    module: 'Module 02 - Core Azure Services'
---

In this walkthrough, we will create a Function App to display a Hello message when there is an HTTP request. 

Estimated time: 30 minutes

**Task 1: Create a Function app**

In this task, we will create a Function app.

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Search for **Function App** and then click **+Add**.

3. Fill in the Azure Function App settings fields. If not specified, take the default. 

    | Settings | Value |
    | -- | --|
    | App name | **function-xxx** (this must be unique) |
    | Subscription | **Choose your subscription** |
    | Resource group | **myRGFunction** (create new) |
    | OS | **Windows** |
    | Hosting plan | **Consumption plan** |
    | Location | **East US** |

4. Select the **Create** button to begin provisioning and deploying your new Azure Function App.

5. Wait for the Notiication that the resource has been created.

6. **Refresh** the Function App page and verify your new resource is *running*. 

    ![Screenshot of the Function App page with the new Function app.](../images/0701.png)

**Task 2: Create a HTTP triggered function and test**

In this task, we will use the Webhook + API function to display a message when there is an HTTP request. 

1. Select your new Function app.

2. Select the "**+**" button next to **Functions**, and select **In-portal**. Notice your other choices for developing in Visual Studio and VS Code. Click **Continue**. 

    ![Screenshot of the choose a development environment step in the azure functions for dot net getting started pane inside Azure portal. The display elements for creating a new in-portal function are highlighted. The highlighted elements are expand the function app, add new function, in-portal, and the continue button.](../images/0702.png)

3. Choose **WebHook + API**, and then select **Create**. This will run a function whenever the app receives an HTTP request. There are a large number of other templates to choose from.

    ![Screenshot of the create a function step in the azure functions for dot net getting started pane inside Azure portal. The webhook + api button and create button are highlighted to illustrate the display elements used to add a new webhook to an Azure function.](../images/0703.png)

4. Notice the code is designed to run an HTTP request and log information. Also, notice the function returns a Hello message with a name. 

    ![Screenshot of the function code. The Hello message is hightlighted.](../images/0704.png)

5. Select **Get function URL** from the top of function editor. 

6. Set the **Key** drop-down value to **default (Function key)**. Then, select **Copy** to copy the function URL. 

    ![Screenshot of the get function URL pane inside the function editor in Azure portal. The display elements get function URL button, set key dropdown, and copy URL button are highlighted to indicate how to obtain and copy the function URL from the function editor.](../images/0705.png)

7. Paste the copied function URL into your web browser's address bar. When the page is requested the function will run. Notice the message that the function needs a name. 

    ![Screenshot of the please provide a name message.](../images/0706.png)

8. Append **&name=yourname** to the end of the URL. 

    **Note**: Here, `<yourname>` refers to your given first name. The final URL will be something like, `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Screenshot of a highlighted function URL and an appended example user name in the address bar of a web browser. The hello message and user name are also highlighted to illustrate the output of the function in the main browser window.](../images/0707.png)

9. When your function runs, trace information is written to log files in Azure. To view the logs in Azure portal, return to the function editor, and select the **Logs** button.

    ![Screenshot of a trace information log resulting from running the function inside the function editor in Azure portal. The logs button for accessing the trace information and some of the log content are highlighted to indicate how to access and read a trace information log from the function editor.](../images/0708.png)

Congratulations! You have created a Function App to display a Hello message when there is an HTTP request. 

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.