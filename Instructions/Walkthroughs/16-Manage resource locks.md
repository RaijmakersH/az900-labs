---
wts:
    title: '16 - Manage resource locks'
    module: 'Module 03 - Security, Privacy, Compliance and Trust'
---
# 16 - Manage resource locks

In this walkthrough, we will create a resource group, add a lock to resource group and test deletion, test deleting a resource in the resource group, and remove the resource lock. 

Estimated time: 15 minutes

# Task 1: Create a resource group

In this task, we will create a resource group for this exercise. 

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Search for and select **Resource groups**, then select **+Add**.

3. Configure a new resource group. When you are done click **Review + create** and then **Create**. 

    | Setting | Value |
    | -- | -- |
    | Subscription | **Use your subscription** |
    | Name | **myRGLocks** |
    | Region | **(US) East US** |
    | | |

# Task 2:  Add a Lock to the resource group and test deletion

In this task, we will add a resource lock to the resource group and test deleting the resource group. 

1. Access your new resource group, **myRGLocks**.

2. You can apply a **Lock** to a subscription, resource group, or individual resource to prevent other users in your organization from accidentally deleting or modifying critical resources. 

3. Under **Settings** click **Locks**, and then click **+Add**. 

    ![Screenshot of the locksrg resource group with the Locks pane displaying.](../images/1601.png)

4. Configure the new lock. When you are done click **OK**. 

    | Setting | Value |
    | -- | -- |
    | Lock name | **RGLock** |
    | Lock Type | **Delete** |
    | | |

5. Select the resource group's **Overview** blade and select **Delete resource group**. Confirm the name of the resource group and click **OK**. You receive an error message stating the resource group is locked and can't be deleted.

    ![Screenshot of the delete locks failed.](../images/1602.png)

# Task 3: Test deleting a member of the resource group

In this task, we will test if the resource lock protects a storage account in the resource group. 

1. Search for **Storage accounts**, and then click **+Add**. 

2. Configure the storage account, then select **Review + Create** and then click **Create**.


    | Setting | Value | 
    | --- | --- |
    | Subscription | **Select your subscription** |
    | Resource group | **myRGLocks** |
    | Storage account name | **storageaccountxxx** (must be unique) |
    | Location | **(US) East US**  |
    | Performance | **Standard** |
    | Account kind | **StorageV2 (general purpose v2)** |
    | Replication | **Locally redundant storage (LRS)** |
    | Access tier (default) | **Hot** |
    | | |

3.  Wait for the notification that the stroage account was successfully created. 

4. Access your new storage account and from the **Overview** pane, click **Delete**. You receive an error message stating the resource or its parent has a delete lock. 

    ![Screenshot of the error deleting the storage account.](../images/1603.png)

    **Note**: Although we did not create a lock specifically for the storage account, we did create a lock at the resource group level, which contains the storage account. As such this *parent* level lock prevents us from deleting the resource, the storage account inherits the lock from the parent.

# Task 4: Remove the resource lock

In this task, we will remove the resource lock and test. 

1. Return to the resource group and under **Settings** select **Locks**.
    
2. Select **Delete** on the lock. 

    ![Screenshot of the Lock with the Delete icon highlighted.](../images/1604.png)

3. Return to your storage account and confirm you can now delete the resource.

Congratulations! You created a resource group, added a lock to resource group and tested deletion, tested deleting a resource in the resource group, and removed the resource lock. 

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.