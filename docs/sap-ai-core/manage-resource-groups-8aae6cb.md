<!-- loio8aae6cbe2c0e4290954b8f61b4b355b7 -->

# Manage Resource Groups

A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.



Resource groups are used to physically isolate machine learning workloads, and to logically isolate related resources for a usage scenario.

When your tenant is onboarded, a default resource group is automatically created. Default resource groups can't be deleted.

As an administrator, you create, edit, or delete resource groups, based on your service consumers and usage scenarios.

Runtime entities such as executions, deployments, configurations, and artifacts belong to a specific resource group and are not shared across resource groups. Scenarios, executables, and Docker registry secrets are shared by all resource groups within a tenant.

A resource group may also be referred to as an instance.

> ### Remember:  
> Your SAP global account may consist of several accounts. Each account can be associated with a tenant. A tenant can contain multiple resource groups. A tenant always contains a default resource group, as well as the resource groups defined for your usage scenarios.

> ### Restriction:  
> The maximum number of resource groups is limited at tenant level to 50. If you reach this limit, you will receive an error message. To free up space, delete some resource groups. Alternatively, raise a ticket to increase your quota.
> 
> For more information, see [Delete a Resource Group](delete-a-resource-group-40d83a2.md).

-   **[Create a Resource Group](create-a-resource-group-01753f4.md "")**  

-   **[Edit a Resource Group](edit-a-resource-group-3f88c30.md "")**  

-   **[Delete a Resource Group](delete-a-resource-group-40d83a2.md "")**  


**Parent topic:**[Administration](administration-7937fc1.md "Creating secrets for external programs and tools, that are used with SAP AI Core means that you can connect them without compromising your credentials.")

<a name="concept_kvy_wbh_wwb"/>

<!-- concept\_kvy\_wbh\_wwb -->

## Resource Group Level Resources

Executables at tenant level are shared across all resource groups. In contrast, runtime entities such as executions, deployments, configurations, and artifacts belong to a specific resource group and cannot be shared across resource groups. Similarly, generic secrets created within a resource group and be used only for workloads within that group.

You can register an object store at resource-group level by setting the resource group header. We recommend that you do not use the same object store bucket with the same IAM user for multiple resource groups.

Example resource group mappings are outlined in the figure below:

![Example resource group mappings.](images/Image_AI_Core_Security_Resource_Group_Mappings_3f54dda.png)

