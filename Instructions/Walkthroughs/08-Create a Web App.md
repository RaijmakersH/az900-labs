---
wts:
    title: '08 - Create a Web App'
    module: 'Module 02 - Core Azure Services'
---
# 08 - Create a Web App

In this walkthrough, we will create a new web app that runs a Docker container. The container displays a Welcome message. 

Estimated time: 25 minutes. 

# Task 1: Create a Web App

Azure App Service is actually a collection of four services, all of which are built to help you host and run web applications. The four services (Web Apps, Mobile Apps, API Apps, and Logic Apps) look different, but in the end they all operate in very similar ways. Web Apps are the most commonly used of the four services, and this is the service that we will be using in this lab.

In this task, you will create an Azure App Service Web App. 

1. Sign-in to the [Azure portal](http://portal.azure.com/). 

2. Search for and select **App Services**.

3. Click **+Add** and configure the web app. Take the defauts for App Service Plan. 

    | Setting | Value |
    | -- | -- |
    | Subscription | **Choose your subscription** |
    | Resource group | **myRGWebApp1** (create new) |
    | Name | **myDockerWebAppxxx** (must be unique) |
    | Publish | **Docker Container** |
    | Operating system | **Linux** |
    | Region | **East US** (ignore any service plan availabiity warnings) |
    | | |	

4. Click **Next > Docker** and configure the container information. The startup command is optional and not need in this exercise. 

    **Note:** This is same container that was used in the Container Instances walkthrough to display a hello world message. 

    | Setting | Value |
    | -- | -- |
    | Options | **Single container** |
    | Image source | **Docker Hub** |
    | Access type | **Public** |
    | Image and tag | **microsoft/aci-helloworld** |
    | | |	


5. Click **Review + create**, and then **Create**. 

# Task 2: Test the Web App

In this task, we will test the web app.

1. Wait for the Web App to deploy.

2. From **Notifications** click **Go to resource**. 

3. In the **Properties** blade, locate the **URL**. 

    ![Screenshot of the web app properties blade. The URL is highlighted.](../images/0801.png)

4. Click on the **URL**, the docker container will run, and the Azure Container Instances page will display.

    ![Screenshot of the Azure Container Instance page.](../images/0802.png)

5. Notice on the **Overview** page for your web app there are several charts. If you run the URL a few times you can begin to view access information. This includes number of requests and average response time. 

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.

