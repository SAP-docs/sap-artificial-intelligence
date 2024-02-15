<!-- loioee90fe114c26439fb0feff9f8f014458 -->

# Multitenancy

SAP AI Core is a tenant-aware BTP reuse service, supporting main tenants and resource groups. Resources are defined for tenants or resource groups as outlined below:

![](images/Multitenancy_diagram_29a8dde.png)

Each main tenant and resource group is mapped to a namespace. The main tenant namespace only contains templates for workflows and model serving. The instances of these objects are created in the respective resource group namespaces and reference the corresponding templates in the main tenant namespace. Each main tenant has a default resource group, which can be used for workloads from the main tenant.



<a name="loioee90fe114c26439fb0feff9f8f014458__section_ezv_jzw_mzb"/>

## Tenant-Level Resources

Tenant-level resources include executables such as:

-   Workflow templates

-   Serving templates

-   Docker registries that contain Docker images

-   User authentication and authorization \(UAA\)


User authentication and authorization are based on the SAP AI Core tenant \(access token obtained using the service key for SAP AI Core\). At runtime or when managing the lifecycle via AI API, the SAP AI Core tenant must set the appropriate resource group in the request header.



<a name="loioee90fe114c26439fb0feff9f8f014458__section_resource_group_level_resources"/>

## Resource-Group-Level Resources

Executables at tenant level are shared across all resource groups. In contrast, runtime entities such as executions, deployments, configurations, and artifacts belong to a specific resource group and cannot be shared across resource groups. Similarly, generic secrets created within a resource group and be used only for workloads within that group.

You can register an object store at resource-group level by setting the resource group header. We recommend that you do not use the same object store bucket with the same IAM user for multiple resource groups.



<a name="loioee90fe114c26439fb0feff9f8f014458__section_i5q_2cx_mzb"/>

## Tenant Isolation of Workloads

Workloads run in a sandbox environment and cannot access workflows of other tenants or resource groups. Only TCP is supported for inbound or outbound traffic from a workload. Opening workloads to open Sockets on UDP ports is strongly discouraged. They are not usable, but may pose a theoretical security problem for the workload.

