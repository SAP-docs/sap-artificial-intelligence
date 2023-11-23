<!-- loio38c4599432d74c1d94e70f7c955a717d -->

# Initial Setup

You provision SAP AI Core from the SAP BTP cockpit in SAP Business Technology Platform. After provisioning, you will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance



<a name="loio38c4599432d74c1d94e70f7c955a717d__prereq_uht_2wv_znb"/>

## Prerequisites

-   Your SAP BTP administrator has access to a global account on SAP Business Technology Platform. For more information, see [Getting a Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d61c2819034b48e68145c45c36acba6e.html).
-   Your SAP BTP administrator has set the entitlement to a subaccount.



<a name="loio38c4599432d74c1d94e70f7c955a717d__context_vjz_rmv_p4b"/>

## Context

The SAP AI Core service is a tenant-aware reuse service. It isolates tenants based on the ID of the zone \(representing the subaccount\). The SAP AI Core service instance is created within a subaccount. Each subaccount represents an SAP AI Core tenant.

> ### Note:  
> The SAP AI Core service does not isolate tenants based on the service instance ID. If you create multiple service instances within the same subaccount, all of them will reference the same SAP AI Core tenant.

![](images/Multitenancy_diagram_29a8dde.png)

The steps below guide you through the provisioning procedure, Alternatively, a booster is available for both SAP AI Core and SAP AI Launchpad. For more information, see [AI Boosters Tutorial](https://developers.sap.com/tutorials/ai-core-launchpad-provisioning.html). If you choose to use the booster, you can skip the remaining steps to [SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md).

1.  [Create a Subaccount](create-a-subaccount-3e3ae83.md "")  

2.  [Enable Cloud Foundry](enable-cloud-foundry-cf0d5d2.md "")  

3.  [Create a Space](create-a-space-4c1190c.md "")  

4.  [Add a Service Plan](add-a-service-plan-86002d9.md "")  

5.  [Create a Service Instance](create-a-service-instance-34761f9.md "")  

6.  [Create a Service Key](create-a-service-key-7323ff4.md "")  

7.  [Use a Service Key](use-a-service-key-3a97465.md)  

8.  [SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md "")  


