<!-- loiodc1e577d98b747a487dc96df03c03bec -->

# Shared Resource Group



## Context

When a consumer creates a service instance of the custom resource, a resource group is automatically created with the ID of the service instance ID. A consumer’s access to resources is restricted to this resource group.

A shared resource group can be used i a service provider wants to manage a central deployment and make it available to all of the service consumers

> ### Restriction:  
> Shared resource groups only allow deployment creation for models available in the `foundation-models` scenario, in generative AI hub.



## Procedure

1.  To enable shared resource group, set `enableSharedResourceGroup` to `true` in the service custom resource.

    > ### Sample Code:  
    > ```
    > ...
    > 	enableSharedResourceGroup: true
    > 	serviceCatalog:
    >     ...
    > ```

    Tenants cannot create, modify or delete a shared resource group using the API. Onboarding for shared resource groups is only possible through the service custom resource..

2.  Check the status of your shared resource group by sending a GET request to the endpoint `{{apiurl}}/v2/admin/services/<service-name>`.

    > ### Sample Code:  
    > ```
    > curl --location '$AI_API_URL/v2/admin/services/aisvc-spam-detection' \
    > --header 'Authorization: Bearer $TOKEN'
    > 
    > # API Response:
    > {
    >     "brokerSecret": {
    >         "name": "broker-credentials",
    >         "passwordKeyRef": "password",
    >         "usernameKeyRef": "username"
    >     },
    >     "capabilities": {
    >         "basic": {
    >             "createExecutions": true,
    >             "staticDeployments": true,
    >             "userDeployments": true
    >         },
    >         "logs": {
    >             "deployments": true,
    >             "executions": true
    >         }
    >     },
    >     "description": "Service exposing AI Content for Spam Detection use-case",
    >     "name": "aisvc-spam-detection",
    >     "serviceCatalog": [
    >         {
    >             "extendCatalog": {
    >                 "bindable": true,
    >                 "description": "Service exposing AI Content for Spam Detection use-case",
    >                 "id": "aisvc-spam-detection-0",
    >                 "name": "aisvc-spam-detection",
    >                 "plans": [
    >                     {
    >                         "description": "Standard plan for Spam Detection Service",
    >                         "free": false,
    >                         "id": "standard",
    >                         "metadata": {
    >                             "supportedPlatforms": [
    >                                 "cloudfoundry",
    >                                 "kubernetes",
    >                                 "sapbtp"
    >                             ]
    >                         },
    >                         "name": "standard"
    >                     }
    >                 ]
    >             },
    >             "extendCredentials": {
    >                 "shared": {
    >                     "serviceUrls": {
    >                         "AI_API_URL": "https://api.ai.internalprod.eu-central-1.aws.ml.hana.ondemand.com"
    >                     }
    >                 }
    >             }
    >         }
    >     ],
    >     "sharedResourceGroupStatus": {
    >         "id": "shared",
    >         "isEnabled": true,
    >         "state": "Provisioned"
    >     },
    >     "status": "PROVISIONED",
    >     "statusMessage": "",
    >     "url": "https://aisvc-425c28c5-aisvc-spam-detection.servicebroker.internalprod.eu-central-1.aws.ml.hana.ondemand.com"
    > }
    > ```




<a name="loiodc1e577d98b747a487dc96df03c03bec__result_p5j_cfj_1fc"/>

## Results

If the `sharedResourceGroupStatus` is `Provisioned`, your shared resource group is provisioned successfully.



<a name="loiodc1e577d98b747a487dc96df03c03bec__postreq_cx4_3fj_1fc"/>

## Next Steps

To add resources to your shared resource group. include the header `AI-Resource-Group: shared`. Consumers accessing service must also use the header `AI-Resource-Group: shared` to access the shared resource group.

