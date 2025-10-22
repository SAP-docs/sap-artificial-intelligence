<!-- loio0619d8ae8e674124ad30fb4f05e308b4 -->

# Enabling the Service in Cloud Foundry

Enable SAP AI Core using the standard procedures for the SAP BTP, Cloud Foundry environment.

> ### Tip:  
> You can use the booster *Set Up Account for SAP AI Core* to automate the steps described in this section on the SAP BTP cockpit. For more information, see [Use Boosters for Free Tier Use of SAP AI Core and SAP AI Launchpad](https://developers.sap.com/tutorials/ai-core-launchpad-provisioning.html).

When you provision SAP AI Core from the SAP BTP cockpit in SAP Business Technology Platform, the system generates a service key. This key contains the URLs and credentials you need to access the SAP AI Core instance.

SAP AI Core is a tenant-aware reuse service that isolates tenants based on the zone ID, which represents the subaccount. When you create an SAP AI Core service instance within a subaccount, it represents an SAP AI Core tenant.

> ### Note:  
> The SAP AI Core service doesn't isolate tenants based on the service instance ID. If you create multiple service instances within the same subaccount, they all reference the same SAP AI Core tenant.

![](images/Multitenancy_diagram_29a8dde.png)

-   **[Create a Subaccount](create-a-subaccount-3e3ae83.md "Create a subsaccount in your global account using the SAP BTP
                                    cockpit.")**  
Create a subsaccount in your global account using the SAP BTP cockpit.
-   **[Enable Cloud Foundry](enable-cloud-foundry-cf0d5d2.md "")**  

-   **[Create a Space](create-a-space-4c1190c.md "")**  

-   **[Add a Service Plan](add-a-service-plan-86002d9.md "Configure the required entitlements to make SAP AI Core accessible in
		your subaccount.")**  
Configure the required entitlements to make SAP AI Core accessible in your subaccount.
-   **[Create a Service Instance](create-a-service-instance-34761f9.md "")**  

-   **[Create a Service Key](create-a-service-key-7323ff4.md "")**  

-   **[Use a Service Key](use-a-service-key-3a97465.md "After you have created your service key, it can be used by local clients, apps in other
		spaces, or entities outside your deployment to access SAP AI Core through one
		of the available interfaces. ")**  
After you have created your service key, it can be used by local clients, apps in other spaces, or entities outside your deployment to access SAP AI Core through one of the available interfaces.

