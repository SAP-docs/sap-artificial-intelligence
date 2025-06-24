<!-- loio38c4599432d74c1d94e70f7c955a717d -->

# Initial Setup

You provision SAP AI Core from the SAP BTP cockpit in SAP Business Technology Platform. After provisioning, you will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance



<a name="loio38c4599432d74c1d94e70f7c955a717d__prereq_uht_2wv_znb"/>

## Prerequisites

-   Your SAP BTP administrator has access to a global account on SAP Business Technology Platform. For more information, see [Getting a Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d61c2819034b48e68145c45c36acba6e.html).
-   Your SAP BTP administrator has set the entitlement to a subaccount.



<a name="loio38c4599432d74c1d94e70f7c955a717d__context_vjz_rmv_p4b"/>

## Context

SAP AI Core is a tenant-aware reuse service that isolates tenants based on the zone ID, which represents the subaccount. When you create an SAP AI Core service instance within a subaccount, it represents an SAP AI Core tenant.

> ### Note:  
> The SAP AI Core service doesn't isolate tenants based on the service instance ID. If you create multiple service instances within the same subaccount, they all reference the same SAP AI Core tenant.

![](images/Multitenancy_diagram_29a8dde.png)

The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both SAP AI Core and SAP AI Launchpad. For more information, see [AI Boosters Tutorial](https://developers.sap.com/tutorials/ai-core-launchpad-provisioning.html). If you choose to use the booster, you can skip the remaining steps to [SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md).

-   **[Enabling the Service in Cloud Foundry](enabling-the-service-in-cloud-foundry-0619d8a.md "Enable SAP AI Core
		using the standard procedures for the SAP BTP Cloud Foundry environment. ")**  
Enable SAP AI Core using the standard procedures for the SAP BTP Cloud Foundry environment.
-   **[Enabling the Service in the Kyma Environment](enabling-the-service-in-the-kyma-environment-8076566.md "Enable SAP AI Core
		using the standard procedures for the SAP BTP
		Kyma
		environment. ")**  
Enable SAP AI Core using the standard procedures for the SAP BTP Kyma environment.

