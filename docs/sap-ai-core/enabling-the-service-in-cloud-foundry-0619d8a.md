<!-- loio0619d8ae8e674124ad30fb4f05e308b4 -->

# Enabling the Service in Cloud Foundry

Enable SAP AI Core using the standard procedures for the SAP BTP Cloud Foundry environment.

You provision SAP AI Core from the SAP BTP cockpit in SAP Business Technology Platform. After you have provisioned the service, you will have your service key, which provides URLs and credentials for accessing the SAP AI Core instance.

SAP AI Core is a tenant-aware reuse service that isolates tenants based on the zone ID, which represents the subaccount. When you create an SAP AI Core service instance within a subaccount, it represents an SAP AI Core tenant.

> ### Note:  
> The SAP AI Core service doesn't isolate tenants based on the service instance ID. If you create multiple service instances within the same subaccount, they all reference the same SAP AI Core tenant.

![](images/Multitenancy_diagram_29a8dde.png)

The steps below guide you through the provisioning procedure. Alternatively, a booster is available for both SAP AI Core and SAP AI Launchpad. For more information, see [AI Boosters Tutorial](https://developers.sap.com/tutorials/ai-core-launchpad-provisioning.html). If you choose to use the booster, you can skip the remaining steps to [SAP AI Core Starter Tutorials](sap-ai-core-starter-tutorials-9795b63.md).

-   **[Create a Subaccount](create-a-subaccount-3e3ae83.md "")**  

-   **[Enable Cloud Foundry](enable-cloud-foundry-cf0d5d2.md "")**  

-   **[Create a Space](create-a-space-4c1190c.md "")**  

-   **[Add a Service Plan](add-a-service-plan-86002d9.md ">")**  
\>
-   **[Create a Service Instance](create-a-service-instance-34761f9.md "")**  

-   **[Create a Service Key](create-a-service-key-7323ff4.md "")**  

-   **[Use a Service Key](use-a-service-key-3a97465.md "After you have configured your  service key, it can be used by local clients, apps in
		other spaces, or entities outside your deployment to access SAP AI Core through one
		of the available interfaces. ")**  
After you have configured your service key, it can be used by local clients, apps in other spaces, or entities outside your deployment to access SAP AI Core through one of the available interfaces.

