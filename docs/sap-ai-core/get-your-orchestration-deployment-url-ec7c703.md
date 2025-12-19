<!-- loioec7c70337ce546bba5f599b7cf639df4 -->

# Get Your Orchestration Deployment URL



<a name="loioec7c70337ce546bba5f599b7cf639df4__prereq_nzn_mdw_tyb"/>

## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](service-plans-c7244c6.md) and [Update a Service Plan](update-a-service-plan-924f892.md).
-   You have completed the client authorization for your preferred user interface. For more information, see [Use a Service Key](use-a-service-key-3a97465.md).




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

