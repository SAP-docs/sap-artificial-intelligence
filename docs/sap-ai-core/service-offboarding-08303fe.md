<!-- loio08303fe594ce48768265235323963283 -->

# Service Offboarding

Tenant offboarding occurs when a customer deletes a subaccount. SAP AI Core polls for the subaccount deletion event and performs the necessary deprovisioning and deletion activities.

> ### Note:  
> Data and resources are not deleted when a service instance is deleted \(because we don't isolate based on the service instance\). If you want to keep the subaccount but still deprovision SAP AI Core, create a **medium** [support ticket](https://launchpad.support.sap.com/#incident/create) on component `CA-ML-AIC` with the title `Service Offboarding` and request that your data and resources be deleted manually.

> ### Remember:  
> When you delete a resource group, [Manage mTLS Certificate Secrets](manage-mtls-certificate-secrets-200810f.md) in that group are deleted. Certificates that were issued before the deletion may remain valid until they expire. You are responsible for removing or revoking trust on any external services that rely on those certificates.

