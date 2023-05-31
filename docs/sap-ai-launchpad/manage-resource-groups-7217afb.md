<!-- loio7217afbcc8cf44ecb9d6f74d0badbe00 -->

# Manage Resource Groups

Resource groups are used to physically isolate machine learning workloads, and to logically isolate related resources for a usage scenario.

When your tenant is onboarded, a default resource group is automatically created. Default resource groups can't be deleted.

As an administrator, you create, edit, or delete resource groups, based on your service consumers and usage scenarios.

Runtime entities such as executions, deployments, configurations, and artifacts belong to a specific resource group and are not shared across resource groups. Scenarios, executables, and Docker registry secrets are shared by all resource groups within a tenant.

A resource group may also be referred to as an instance.

> ### Remember:  
> Your SAP global account may consist of several accounts. Each account can be associated with a tenant. A tenant can contain multiple resource groups. A tenant always contains a default resource group, as well as the resource groups defined for your usage scenarios.

-   **[Create a Resource Group](create-a-resource-group-060d9be.md "As an administrator, you create resource groups to isolate your ML workloads and processes.")**  
As an administrator, you create resource groups to isolate your ML workloads and processes.
-   **[Edit a Resource Group](edit-a-resource-group-7c554d2.md "As an administrator, you can edit resource groups used within your AI processes. You can change labels and values, or add, edit, or remove
		object store secrets associated with the resource group.")**  
As an administrator, you can edit resource groups used within your AI processes. You can change labels and values, or add, edit, or remove object store secrets associated with the resource group.
-   **[Delete a Resource Group](delete-a-resource-group-dc5373a.md "As an administrator, you delete resource groups which contain errors or which are no longer required in your AI processes.")**  
As an administrator, you delete resource groups which contain errors or which are no longer required in your AI processes.

**Related Information**  


[Resource Groups](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/26c6c6b50e3f412f8bc0cd6a8ebdb850.html#loio26c6c6b50e3f412f8bc0cd6a8ebdb850 "SAP AI Core tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.") :arrow_upper_right:

[Manage Resource Groups](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/8aae6cbe2c0e4290954b8f61b4b355b7.html "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.") :arrow_upper_right:

