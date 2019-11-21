---
wts:
    title: '04 - Create blob storage'
    module: 'Module 02 - Core Azure Services'
---
# 04 - Create blob storage

In this walkthrough, we will create a storage account, then work with blob storage files.

Estimated time: 25 minutes. 

# Task 1: Create a storage account

In this task, we will create a new storage account. 

1. Sign in to the Azure portal at <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Search for and select **Storage accounts**, and then click **+Add**. 

3. Complete the Create storage account **Basics** blade with the following details.


    | Setting | Value | 
    | --- | --- |
    | Subscription | **Choose your subscription** |
    | Resource group | **myRGStorage** (create new) |
    | Storage account name | **storageaccountxxx** (must be unique) |
    | Location | **(US) East US**  |
    | Performance | **Standard** |
    | Account kind | **StorageV2 (general purpose v2)** |
    | Replication | **Locally redundant storage (LRS)** |
    | Access tier (default) | **Hot** |
    | | |

5. Select **Review + Create** to review your storage account settings and allow Azure to validate the configuration. 

6. Once validated select **Create**. Wait for the notification that the account was successfully created. 

7. Search for **Storage accounts** and ensure your new storage account is listed.

    ![Screenshot of the newly created storage account in the Azure portal .](../images/0401.png)

# Task 2: Work with blob storage

In this task, we will create a Blob container and upload a blob file. 

1. Click your new storage account and scroll to the **Blob** service section, and then select **Containers**.

2. Click **+Container** and complete the information. Use the Information icons to learn more. When done click **OK**.


    | Setting | Value |
    | --- | --- |
    | Name | **blob1**  |
    | Public access level| **Private (no anonymous access)** |
    | | |

    ![Screenshot of the newly created blob container in the storage account in the Azure portal.](../images/0402.png)

4. Select the **blob1** container, and then click **Upload**.

5. Browse to a file on your local computer. If you do not have a file create a simple `.txt` file. 

6. Click on the **Advanced** arrow, leave the default values but note your options, and then select **Upload**.

    **Note**: You can upload as many blobs as you like in this way. New blobs will be listed within the container.

7. Once the file is uploaded, right-click on the file and notice the options including Edit/View, Download, Blob properties, and Delete. 

8. As you have time, return to your storage account and review the options for Files, Tables, and Queues.

# Task 3: Monitor the storage account

1. Return to the main storage account page.

2. Click **Diagnose and solve problems**. 

3. Explore some of the most common storage problems. Notice there is a troubleshooter.

4. Click **Insights (Preview)**. Notice there is information on Failures, Performance, Availability, and Capacity. Your information will be different.

    ![Screenshot of the storage account Insights page.](../images/0403.png)

Congratulations! You have created a storage account, then worked with blob storage files.

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.