---
wts:
    title: '05 - Create a SQL database'
    module: 'Module 02 - Core Azure Services'
---

# 05 - Create a SQL database

In this walkthrough, we will create a SQL database in Azure and then query the data in that database.

Estimated time: 25 minutes

# Task 1: Create the database

In this task, we will create a new SQL database using the AdventureWorksLT sample database. 

1. Sign in to the Azure portal at <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Search for and select **SQL databases**, and then click **+Add**. 

3. On the **Basics** tab, fill in this information.  

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Choose your subscription** |
    | Resource group | **myRGDb** (create new) |
    | Database name| **db1** | 
    | | |

3. Next to **Server** click **Create new** and enter this information. Click **OK** when finished.

    | Setting | Value | 
    | --- | --- |
    | Server name | **sqlserverxxx** (must be unique) | 
    | Server admin login | **sqluser** |
    | Password | **Pa$$w0rd1234** |
    | Location | **(US) East US** |
    | Allow Azure services to access server | **Check the box** |
    | | |

   ![Screenshot of the Server pane and the New Server pane with fields filled in as per the table and the Select button highlighted.](../images/0501.png)

4. Move to the **Additional settings** tab. We will be using the AdventureWorksLT sample database.

    | Setting | Value | 
    | --- | --- |
    | Use existing data | **Sample** | 
    | | |

5. Click **Review + create** and then **Create** to deploy and provision the resource group, server, and database. It can take approx. 2 to 5 minutes to deploy.

6. Monitor your deployment. 

# Task 2: Test the database.

In this task, we will configure the SQL server and run a SQL query. 

1. Search for **SQL databases** and ensure your new database was created. You may need to **Refresh** the page.

    ![Screenshot of the SQL database and server that have just been deployed.](../images/0502.png)

2. Open the SQL database you created **db1**, and then select **Query Editor (preview)**.

3. Login as **sqluser** with the password **Pa$$w0rd1234**.

4. You will not be able to login. Read the error closely and make note of the IP address that needs to be allowed through the firewall. 

    ![Screenshot of the Query Editor login page with IP address error.](../images/0503.png)

5. Search for **SQL servers**, and select your SQL server. 

    ![Screenshot of the SQL server page.](../images/0504.png)

6. From the SQL server **Overview** blade, click **Show firewall settings**.

7. Click **Add client IP** (top menu bar) and add your IP address from the error page. Be sure to **Save** your changes. 

    ![Screenshot of the SQL server firewall settings page with the new IP rule highlighted.](../images/0506.png)

8. Return to your SQL database and the Query Editor (Preview) login page. Try to login again as **sqluser** with the password **Pa$$w0rd1234**. This time you should succeed. Note that it may take a couple of minutes for the new firewall rule to be deployed. 

9. Once you log in successfully the query pane appears, enter the following query into the editor pane.

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Screenshot of the Query editor with the query pane and the commands executing successfully.](../images/0507.png)

4. Select **Run**, and then review the query results in the **Results** pane. The query should run successfully.

    ![Screenshot of the database Query Editor pane with the SQL code having been run successfully and the output visible in the results pane.](../images/0508.png)

Congratulations! You have created a SQL database in Azure and successfully queried the data in that database.

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.