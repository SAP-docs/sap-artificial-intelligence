<!-- loiob32e7a85f9e143c1924f31533ee81697 -->

# Create a Deployment for a Generative AI Model

You make a generative AI model available for use by creating a deployment. You can do so one time for each model and model version, and for each resource group that you want to use with generative AI hub. The deployment URL that is generated can be reused.



<a name="loiob32e7a85f9e143c1924f31533ee81697__prereq_nzn_mdw_tyb"/>

## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](service-plans-c7244c6.md) and [Update a Service Plan](update-a-service-plan-924f892.md).



<a name="loiob32e7a85f9e143c1924f31533ee81697__context_ll5_4jw_tyb"/>

## Context

You make a model available for use by creating a deployment. You can do so one time for each model and model version. The model deployment includes the `modelName` and `version` of the model you want to access. After the deployment is complete, you have a `deploymentUrl`, which can be used across your organization to access the model version.

<a name="task_m15_5kw_tyb"/>

<!-- task\_m15\_5kw\_tyb -->

## Using the API





<a name="task_m15_5kw_tyb__steps_n15_5kw_tyb"/>

## Procedure

1.  Decide which LLM you want to deploy and note the following information:

    -   Executable ID

    -   Model name

    -   Model version

        > ### Note:  
        > -   Instead of specifying a model version, using “latest” will use the latest version of the model available in SAP AI Core.
        > 
        > -   Where model version is not listed, it is not applicable.


    **For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**

2.  Check that you have access to the scenario containing generative AI by sending a GET request to `{{apiurl}}/v2/lm/scenarios`.

    > ### Note:  
    > You must use the same resource group for all of your generative AI activities. To use a different resource group, these steps must be repeated for each resource group.For more information, see [Manage Resource Groups](manage-resource-groups-8aae6cb.md).

    ```
    curl --location '{{apiurl}}/v2/lm/scenarios' \
    --header 'AI-Resource-Group: default' \
    --header "Authorization: Bearer $AUTH_TOKEN"
    ```

    The scenarios listed contain a scenario with the id `foundation-models`.

3.  Create a configuration by sending a POST request to the endpoint `{{apiurl}}/v2/lm/configurations`.

    Include details of the model to which you want to provide access by passing in the following parameters:

    -   `name` is your free choice of identifier.

    -   `executableId`, `modelName`, and `modelVersion` are provided in SAP Note [3437766](https://me.sap.com/notes/3437766).

    -   `scenarioId` must be `foundation-models`.

    -   `versionId` is your own version reference.


    > ### Sample Code:  
    > ```
    > curl --location '$AI_API_URL/lm/configurations' \
    > --header 'AI-Resource-Group: default' \
    > --header 'Content-Type: application/json' \
    > --header "Authorization: Bearer $AUTH_TOKEN" \
    > --data '{
    > 	"name": "yourNameChoice",
    > 	"executableId": "<executableId>",
    > 	"scenarioId": "foundation-models",
    > 	"versionId": "0.0.1",
    > 	"parameterBindings": [
    > 		{
    > 			"key":"modelName",
    > 			"value":"<ModelName>"
    > 		},
    > 		{
    > 			"key": "modelVersion",
    > 			"value": "<ModelVersion>"
    > 		}
    >   ]
    > }'
    >    
    > ```

    > ### Tip:  
    > You can specify the value `latest` for the `modelVersion` to use the most recent model version available in SAP AI Core.

    You receive a unique `configurationId` in the response.

4.  Create a deployment by sending a POST request to the endpoint `{{apiurl}}/v2/lm/deployments`.

    Include the `configurationId` from the previous step in your request.

    > ### Sample Code:  
    > ```
    > curl --location '$AI_API_URL/lm/deployments' \
    > --header 'AI-Resource-Group: default' \
    > --header 'Content-Type: application/json' \
    > --header "Authorization: Bearer $AUTH_TOKEN" \
    > --data '{
    >  "configurationId": "yourConfigurationId"
    > }'
    > ```

5.  Retrieve the details of your deployment by sending a GET request to the endpoint`{{apiurl}}/v2/lm/deployments`.

    ```
    curl --location 'AI_API_URL/v2/lm/deployments/<deploymentID>' \
    --header 'AI-Resource-Group: default' \
    --header "Authorization: Bearer $AUTH_TOKEN"
    ```




<a name="task_m15_5kw_tyb__postreq_yrz_5cd_5yb"/>

## Next Steps

When the deployment is running, the model can be accessed using the `deploymentUrl` provided in the response. For more information, see [Consume Generative AI Models](consume-generative-ai-models-bf0373b.md).

<a name="concept_fn1_2qy_szb"/>

<!-- concept\_fn1\_2qy\_szb -->

## Model Lifecycle

Model versions have deprecation dates. Where a model version is specified in a deployment, the deployment will stop working on the deprecation date of that model version.

Implement one of the following model upgrade options:

-   **Auto Upgrade:** Create a new generative AI configuration and deployment or patch a deployment with a new configuration, specifying `modelVersion` `latest`. When a new `modelVersion` is supported by SAP AI Core, existing generative AI deployments will automatically use the latest version of the given model.

-   **Manual Upgrade:** Create a new generative AI configuration with your chosen replacement `modelVersion` and use it to patch your deployment. This model version will be used in generative AI deployments irrespective of updates to the models supported by SAP AI Core.

    > ### Note:  
    > If `modelVersion` isn’t specified, it will be `latest` by default. To upgrade manually, you **must** specify a `modelVersion`.


