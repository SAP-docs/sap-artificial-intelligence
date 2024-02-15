<!-- loio26c6c6b50e3f412f8bc0cd6a8ebdb850 -->

# Resource Groups

SAP AI Core tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.

Resource groups represent a virtual collection of related resources within the scope of one SAP AI Core tenant. When your tenant is onboarded, a default resource group is created immediately. Further resource groups can be created, or deleted by your tenant administrator with the AI API. Tenants can map the resource groups based on the corresponding usage scenarios.

If your SAP AI Core tenant uses resource groups to isolate the scenario consumer tenant and the resource groups are subsequently deleted, the scenario consumers will be deprovisioned. SAP AI Core is not aware of the scenario consumer of the tenant. The standard XUSAA multitenancy model is followed.

-   **[Scope of Resources](scope-of-resources-c9518c0.md "Resources that are available for tenants and resource groups differ based on the
		available scope.")**  
Resources that are available for tenants and resource groups differ based on the available scope.

