---
wts:
    title: '14 - Create an Azure Policy'
    module: 'Module 03 - Security, Privacy, Compliance and Trust'
---
# 14 - Create an Azure Policy

In this walkthrough, we will create an Azure Policy to restrict deployment of Azure resources to a specific location.

Estimated time: 20 minutes

# Task 1: Create a Policy assignment

In this task, we will configure the Allowed location policy and assign it to our subscription. 

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Search for and select **Policy**, under the **Authoring** section click **Definitions**.  Take a moment to review the list of built-in policy definitions. For example, in the **Category** drop-down select only **Compute**. Notice the **Allowed virtual machine SKUs** definition enables you to specify a set of virtual machine SKUs that your organization can deploy.

3. Return to the **Policy** page, under the **Authoring** section click **Assignments**. An assignment is a policy that has been assigned to take place within a specific scope. For example, a definition could be assigned to the subscription scope. 

4. Select **Assign Policy** from the top of the **Policy - Assignments** page.

5. On the **Assign Policy** page, select the Scope selector by clicking the ellipsis.

    ![Screenshot of the scope selector ellipses.](../images/1401.png)

6. Ensure your subscription is selected. Your subscription will be different. Notice you can optionally scope the policy to a resource group. Leave the defaults and click **Select**. 

    **Note**: A scope determines what resources or grouping of resources the policy assignment gets enforced on. In our case we could assign this policy to a specific resource group, however we will assign the policy at subscription level. Also, be aware that resources can be excluded based on the Scope. Exclusions are optional.

    ![Screenshot of the Scope pane with field values filled in and the Select button highlighted. ](../images/1402.png)

7. Select the **Policy definition** ellipsis button.  In the **Search** box type **location** and click on the  **Allowed locations** definition, then click **Select**.

    **Note**: This **Allowed Locations** policy definition will specify a location into which all resources must be deployed. If a different location is chosen deployment will not be allowed. For more information view the [Azure Policy Samples](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index) page.

   ![Screenshot of Available Definitions pane with various fields highlighted and the Audit VMs that do not use managed disks option selected.](../images/1403.png)

8.  In the **Assign policy** pane, in the **PARAMETERS** tab, click on the arrow at the end of the **Allowed locations** box and from the subsequent list choose **Japan West**. Leave all other values as they are and Click **Review + save**, and then **Save**.

    ![Screenshot of Assign policy pane with various fields filled in along with the location Japan West populated and the assign button highlighted.](../images/1404.png)

9. The **Allowed locations** policy assignment is now listed on the **Policy - Assignments** pane and it is now in place and available to enforce at the scope level we specified (subscription level).

   ![Screenshot of Policy - Assignments pane with the allowed locations assignment highlighted.](../images/1406.png)

# Task 2: Test Allowed location policy

In this task, we will test the Allowed location policy. 

1. In the Azure Portal, search for and select **Storage accounts**, and then click **+Add**.

2. Configure the storage account. Take the defaults for the other settings. 

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Use your subscription** |
    | Resource group | **myRGPolicy** (create new) |
    | Storage account name | **storageaccountxxx** (must be unique) |
    | Location | **(US) East US** |
    | | |

3. Click **Review + create**.

4. You will receive a Validation failed message, and click on the **Click here to view details** message. In the resultant **Errors** blade, on the **Summary** tab note the error message, **Resource xyz was disallowed by Policy** and the policy name listed as **Allowed locations**

    **Note**: You can dig in further for specifics, by clicking on the **Raw Error** tab and viewing the output and also by clicking on the Allowed locations policy, to view the policy that blocked the deployment.

    ![Screenshot of disallowed due to policy error.](../images/1406.png)


# Task 3: Delete the policy assignment

In this task, we will remove the Allowed location policy assignment and test. 

We will delete the policy assignment to ensure we are not blocked on any future work we wish to do.

1. In the portal, search for and select **Policy**, and then click your **Allowed locations** policy.

2. Notice you can view the compliance state of the various policies you have assigned.

    **Note**: The Allowed location policy may show non-compliant resources. If so, these are resources created prior to the policy assignment.

3. Select **Delete Assignment** from the top menu.

   ![Screenshot of the Delete Assignment menu item.](../images/1407.png)

4. Confirm you wish to delete the policy assignment in the **Delete assignment** dialogue by clicking **Yes**

5. Try to create another storage account to ensure the policy is no longer in effect.

    **Note**: Some scenarios where the **Allowed locations** policy can be useful include: 
    - *Cost Tracking*: You could have different subscriptions for different regional locations and ensuring that all resources are deployed in that region to help cost tracking. 
    - *Data Residency and Security compliance*: You could also have data residency requirements, and create subscriptions per customer or specific workloads, and define that all resources must be deployed in a particular datacenter to ensure data and security compliance requirements.

Congratulations! You have created an Azure Policy to restrict deployment of Azure resources to a particular datacenter.

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.