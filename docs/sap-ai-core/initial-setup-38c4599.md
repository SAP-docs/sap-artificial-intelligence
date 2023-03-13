<!-- loio38c4599432d74c1d94e70f7c955a717d -->

# Initial Setup

You provision SAP AI Core via the SAP BTP cockpit in SAP Business Technology Platform.



<a name="loio38c4599432d74c1d94e70f7c955a717d__prereq_uht_2wv_znb"/>

## Prerequisites

Your SAP BTP administrator has access to a global account on SAP Business Technology Platform. For an overview of the required steps, see [Getting a Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d61c2819034b48e68145c45c36acba6e.html).

Your SAP BTP administrator has set the entitlement to a subaccount so that you can provision SAP AI Core.



<a name="loio38c4599432d74c1d94e70f7c955a717d__context_vjz_rmv_p4b"/>

## Context

The SAP AI Core service is a tenant-aware reuse service and implements tenant isolation based on identity zone ID \(representing the subaccount\). The SAP AI Core service instance is created within a subaccount. Each subaccount represents an SAP AI Core tenant.

> ### Note:  
> The SAP AI Core service does not implement tenant isolation based on service instance ID. This means that if a customer creates multiple SAP AI Core service instances within the same subaccount, all the service instances will reference the same SAP AI Core tenant.

Once SAP AI Core has been provisioned and you have access to the service key, you no longer need to follow these steps. The service key provides URLs and credentials that let you access the SAP AI Core instance through an external HTTP client \(such as Postman\) or through curl.

-   **[Create a Subaccount](create-a-subaccount-3e3ae83.md "")**  

-   **[Enable Cloud Foundry](enable-cloud-foundry-cf0d5d2.md "")**  

-   **[Create a Space](create-a-space-4c1190c.md "")**  

-   **[Add a Service Plan](add-a-service-plan-86002d9.md "")**  

-   **[Create a Service Instance](create-a-service-instance-34761f9.md "")**  

-   **[Create a Service Key](create-a-service-key-7323ff4.md "")**  

-   **[SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md "")**  


