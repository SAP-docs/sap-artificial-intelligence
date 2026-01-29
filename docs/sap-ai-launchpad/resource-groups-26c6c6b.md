<!-- loio26c6c6b50e3f412f8bc0cd6a8ebdb850 -->

# Resource Groups

Tenants use resource groups to isolate related ML resources and workloads. Scenarios, executables, and Docker registry secrets are shared across all resource groups.

Resource groups represent a virtual collection of related resources within the scope of one tenant. When a tenant is onboarded, the system immediately creates a default resource group. Tenant administrators can create or delete additional resource groups using the AI API. Tenants can map resource groups based on corresponding usage scenarios.

If a tenant uses resource groups to isolate scenario consumer tenants and those resource groups are deleted, the scenario consumers are deprovisioned. The service does not recognize the scenario consumer of the tenant. The standard XSUAA multitenancy model is followed.

