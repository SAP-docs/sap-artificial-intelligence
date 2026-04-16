<!-- loioec7c70337ce546bba5f599b7cf639df4 -->

# Get An Orchestration Deployment URL



<a name="loioec7c70337ce546bba5f599b7cf639df4__prereq_nzn_mdw_tyb"/>

## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right: and [Update a Service Plan](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/924f892e67b7443fbb4476b3e81959b2.html "Update your SAP AI Core service instance from the free plan to a standard or extended plan while keeping your data and models.") :arrow_upper_right:.
-   You have completed the client authorization for your preferred user interface. For more information, see [Use a Service Key](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/3a97465bf6164400a4b5c1641007e3d6.html "After you have created your service key, it can be used by local clients, apps in other spaces, or entities outside your deployment to access SAP AI Core through one of the available interfaces.") :arrow_upper_right:.




## Context

Your default resource group contains a running orchestration deployment. You can use this URL across your organization to access orchestration in the generative AI hub.



## Procedure

1.  Send a GET request to the endpoint `$AI_API_URL/v2/lm/deployments` and include the default resource group in the header.

    ```
    curl --request GET $AI_API_URL/v2/lm/deployments \
        --header "Authorization: Bearer $TOKEN" \
        --header "AI-Resource-Group: default"  
    ```

2.  In the response, search for the deployment object where the `configurationName` is `defaultOrchestrationConfig`, and note the `deploymentUrl` associated with this deployment.

3.  Set the value of the returned `deploymentUrl` as an environment variable.

    ```
    ORCH_DEPLOYMENT_URL="<deployment_url>"
    ```




<a name="loioec7c70337ce546bba5f599b7cf639df4__postreq_izz_rwh_42c"/>

## Next Steps

If you cannot locate a RUNNING orchestration deployment, or would like to create additional orchestration deployments, see [Create a Deployment for Orchestration](create-a-deployment-for-orchestration-4387aa7.md)

