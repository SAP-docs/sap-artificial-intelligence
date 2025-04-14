<!-- loio4387aa7a9fa44402822ad6bc3631f846 -->

# Create a Deployment for Orchestration





<a name="loio4387aa7a9fa44402822ad6bc3631f846__prereq_nzn_mdw_tyb"/>

## Prerequisites

> ### Note:  
> It is likely that you already have an orchestration deployment running in your default resource group. These steps are only required for users who do not have an orchestration deployment. For more information, see [Get Your Orchestration Deployment URL](get-your-orchestration-deployment-url-ec7c703.md).

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](service-plans-c7244c6.md) and [Update a Service Plan](update-a-service-plan-924f892.md).
-   You have completed the client authorization for your preferred user interface. For more information, see [Use a Service Key](use-a-service-key-3a97465.md).




<a name="loio4387aa7a9fa44402822ad6bc3631f846__context_oqk_24g_c2c"/>

## Context

You create a deployment to make orchestration capabilities available for use. After the deployment is complete, you get a `deploymentUrl`. You can use this URL across your organization to access orchestration in the generative AI hub.

For more information, see [Consumption of GenAI Models Using Orchestration – A Beginner's Guide](https://developers.sap.com/tutorials/ai-core-orchestration-consumption.html)as well as [Libraries and SDKs](libraries-and-sdks-499309d.md).



<a name="loio4387aa7a9fa44402822ad6bc3631f846__steps_cdn_ycz_bcc"/>

## Procedure

1.  Create a configuration for the orchestration deployment.

    Orchestration is exposed via the global scenario `orchestration` and the executable `orchestration`.

    1.  Send the following request:

        ```
        curl --request POST "$AI_API_URL/v2/lm/configurations" \
          --header "Authorization: Bearer $TOKEN" \
          --header "ai-resource-group: $RESOURCE_GROUP" \
          --header "Content-Type: application/json" \
          --data-raw  '{ 
            "name": "orchestration-config", 
            "executableId": "orchestration", 
            "scenarioId": "orchestration"
          }'
        ```

        The response appears as follows:

        > ### Output Code:  
        > ```
        > {
        >   "id": "f7ac7f77-e70f-4e9c-86b5-1504b44fe789",
        >   "message": "Configuration created"
        > }
        > ```

    2.  Take the `id` of the configuration and set it as an environment variable.

        ```
        ORCH_CONFIG_ID=f7ac7f77-e70f-4e9c-86b5-1504b44fe789
        ```


2.  Create the deployment for orchestration using the configuration `id`:

    1.  Send the following request:

        ```
        curl --request POST $AI_API_URL/v2/lm/deployments \
            --header 'content-type: application/json' \
            --header "Authorization: Bearer $TOKEN" \
            --header "ai-resource-group: $RESOURCE_GROUP" \
            --data-raw "{
                \"configurationId\": \"$ORCH_CONFIG_ID\"
            }"
        ```

        The response appears as follows:

        > ### Output Code:  
        > ```
        > {
        >   "deploymentUrl": "",
        >   "id": "d4168482710c6cf9",
        >   "message": "Deployment scheduled.",
        >   "status": "UNKNOWN"
        > }
        > ```

    2.  Take the `id` of the deployment response and set it as an environment variable.

        ```
        ORCH_DEPLOYMENT_ID=d4168482710c6cf9
        ```


3.  Wait for the deployment to start.

    It takes a few minutes for the orchestration deployment to reach the status RUNNING. You can check the status of the deployment using the deployment `id`.

    ```
    curl --request GET "$AI_API_URL/v2/lm/deployments/$ORCH_DEPLOYMENT_ID" \
        --header "Authorization: Bearer $TOKEN" \
        --header "ai-resource-group: $RESOURCE_GROUP"
    ```

    If the output looks as follows \(that is, the status is RUNNING\), the deployment is ready. If not, try again after a couple of minutes.

    ```
    {
      "configurationId": "f7ac7f77-e70f-4e9c-86b5-1504b44fe789",
      "configurationName": "orchestration-config",
      "createdAt": "2024-06-20T14:40:16Z",
      "deploymentUrl": ,
      "details": {
        "resources": {
          "backend_details": {}
        },
        "scaling": {
          "backend_details": {}
        }
      },
      "id": "d4468482710c6cf9",
      "lastOperation": "CREATE",
      "latestRunningConfigurationId": "f7ac7f77-e70f-4e9c-86b5-1504b44fe789",
      "modifiedAt": "2024-06-20T14:48:03Z",
      "scenarioId": "llm-orchestration",
      "startTime": "2024-06-20T14:41:22Z",
      "status": "RUNNING",
      "submissionTime": "2024-06-20T14:40:18Z",
      "targetStatus": "RUNNING"
    }
    ```

4.  Set the value of the returned `deploymentUrl` as an environment variable.

    The `deploymentUrl` is available only when the deployment has the status RUNNING.

    ```
    ORCH_DEPLOYMENT_URL="<deployment_url>"
    ```


