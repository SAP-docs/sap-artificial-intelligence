<!-- loio7217afbcc8cf44ecb9d6f74d0badbe00 -->

# Manage Resource Groups



Resource groups are used to physically isolate machine learning workloads, and to logically isolate related resources for a usage scenario.

When your tenant is onboarded, a default resource group is automatically created. Default resource groups can't be deleted.

As an administrator, you create, edit, or delete resource groups, based on your service consumers and usage scenarios.

Runtime entities such as executions, deployments, configurations, and artifacts belong to a specific resource group and aren't shared across resource groups. Scenarios, executables, and Docker registry secrets are shared by all resource groups within a tenant.

A resource group is also referred to as an instance.

> ### Remember:  
> Your SAP global account can consist of several accounts. Each account can be associated with a tenant. A tenant can contain multiple resource groups. A tenant always contains a default resource group, as well as the resource groups defined for your usage scenarios.

> ### Note:  
> The maximum number of resource groups is limited at tenant level to 50. If you reach this limit, you receive an error message. To free up space, delete some resource groups. Alternatively, raise a ticket to increase your quota.

-   **[Create a Resource Group](create-a-resource-group-060d9be.md "As an administrator, you create resource groups to isolate your ML workloads and processes.")**  
As an administrator, you create resource groups to isolate your ML workloads and processes.
-   **[Edit a Resource Group](edit-a-resource-group-7c554d2.md "As an administrator, you can edit resource groups used within your AI processes. You can change labels and values, or add, edit, or remove
		object store secrets associated with the resource group.")**  
As an administrator, you can edit resource groups used within your AI processes. You can change labels and values, or add, edit, or remove object store secrets associated with the resource group.
-   **[Delete a Resource Group](delete-a-resource-group-dc5373a.md "As an administrator, you delete resource groups which contain errors or which are no longer required in your AI processes.")**  
As an administrator, you delete resource groups which contain errors or which are no longer required in your AI processes.

**Related Information**  


[Resource Groups](resource-groups-26c6c6b.md "Tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.")

