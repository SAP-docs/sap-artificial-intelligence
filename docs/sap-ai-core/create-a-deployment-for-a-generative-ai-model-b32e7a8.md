<!-- loiob32e7a85f9e143c1924f31533ee81697 -->

# Create a Deployment for a Generative AI Model

You make a generative AI model available for use by creating a deployment. You can do so one time for each model and model version, and for each resource group that you want to use with Generative AI Hub. The deployment URL that is generated can be reused.



<a name="loiob32e7a85f9e143c1924f31533ee81697__prereq_nzn_mdw_tyb"/>

## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/e2eb894cbc6445f99784ccd973d2ddee/CLOUD/en-US/388a9de7fc2442f7891be5b607cb137e.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts. The generative AI hub in SAP AI Core is available only through the sap-internal service plan.") :arrow_upper_right: and [Update a Service Plan](update-a-service-plan-924f892.md).
-   You have completed the client authorization for your preferred user interface. For more information, see [Use a Service Key in SAP AI Core](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/3a97465bf6164400a4b5c1641007e3d6.html?locale=en-US&state=DRAFT&version=CLOUD).




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



    <table>
    <tr>
    <th valign="top">

    Executable ID
    
    </th>
    <th valign="top">

    Model Name
    
    </th>
    <th valign="top">

    Model Version
    
    </th>
    <th valign="top">

    Deprecation \(as Specified by Model Provider\)

    YYYY-MM-DD
    
    </th>
    <th valign="top">

    Region
    
    </th>
    <th valign="top">

    Request Limit \(Requests per Minute\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    azure-openai
    
    </td>
    <td valign="top">
    
    gpt-35-turbo
    
    </td>
    <td valign="top">
    
    0613
    
    </td>
    <td valign="top">
    
    2024-06-13
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    120
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    azure-openai
    
    </td>
    <td valign="top">
    
    gpt-35-turbo-16k
    
    </td>
    <td valign="top">
    
    0613
    
    </td>
    <td valign="top">
    
    2024-06-13
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    96
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    azure-openai
    
    </td>
    <td valign="top">
    
    gpt-4
    
    </td>
    <td valign="top">
    
    0613
    
    </td>
    <td valign="top">
    
    2024-07-05
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    18
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    azure-openai
    
    </td>
    <td valign="top">
    
    gpt-4-32k
    
    </td>
    <td valign="top">
    
    0613
    
    </td>
    <td valign="top">
    
    2024-07-05
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    78
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    azure-openai
    
    </td>
    <td valign="top">
    
    text-embedding-ada-002
    
    </td>
    <td valign="top">
    
    2
    
    </td>
    <td valign="top">
    
    2025-04-04
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    138
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    aicore-opensource
    
    </td>
    <td valign="top">
    
    tiiuae--falcon-40b-instruct
    
    </td>
    <td valign="top">
    
     
    
    </td>
    <td valign="top">
    
     
    
    </td>
    <td valign="top">
    
    -   US10 \(mapped to Azure US East\)
    -   EU10 \(mapped to Azure EU Central\)


    
    </td>
    <td valign="top">
    
    138
    
    </td>
    </tr>
    </table>
    
2.  Check that you have access to the scenario containing generative AI by sending a GET request to `{{apiurl}}/v2/lm/scenarios`.

    Set the *Authorization* header with `Bearer $TOKEN` and set your resource group.

    > ### Note:  
    > You must use the same resource group for all of your generative AI activities. To use a different resource group, these steps must be repeated for each resource group.

    ![](images/Scenarios_0cf13f1.png)

    The scenarios listed contain a scenario with the id `foundation-models`.

3.  Create a configuration by sending a POST request to the endpoint `{{apiurl}}/v2/lm/configurations`.

    Include details of the model to which you want to provide access by passing in the following parameters:

    -   `name` is your free choice of identifier.

    -   `executableId`, `modelName`, and `modelVersion` are provided in the table above.

    -   `scenarioId` must be `foundation-models`.

    -   `versionId` is your own version reference.


    > ### Sample Code:  
    > ```
    > {
    > 	"name": "yourNameChoice",
    > 	"executableId": "azure-openai",
    > 	"scenarioId": "foundation-models",
    > 	"versionId": "0.0.1",
    > 	"parameterBindings": [
    > 		{
    > 			"key":"modelName",
    > 			"value":"gpt-35-turbo"
    > 		},
    > 		{
    > 			"key": "modelVersion",
    > 			"value": "0613"
    > 		}
    >   ],
    > 	"inputArtifactBindings": []
    > }
    >    
    > ```

    ![](images/Config_e45479e.png)

    > ### Tip:  
    > You can specify the value `latest` for the `modelVersion` to use the most recent model version available in SAP AI Core.

    You receive a unique `configuationId` in the response.

4.  Create a deployment by sending a POST request to the endpoint `{{apiurl}}/v2/lm/deployments`.

    Include the `configuationId` from the previous step in your request.

    > ### Sample Code:  
    > ```
    > {
    >  "configurationId": "yourConfigurationId"
    > }
    > ```

    ![](images/deploy_dad14bc.png)

5.  Retrieve the details of your deployment by sending a GET request to the endpoint`{{apiurl}}/v2/lm/deployments`.

    ![](images/check_depl_49c1cae.png)




<a name="task_m15_5kw_tyb__postreq_yrz_5cd_5yb"/>

## Next Steps

When the deployment is running, the model can be accessed using the `deploymentUrl` provided in the response. For more information, see [Consume Generative AI Models](consume-generative-ai-models-bf0373b.md).

<a name="concept_fn1_2qy_szb"/>

<!-- concept\_fn1\_2qy\_szb -->

## Model Lifecycle

Model versions have deprecation dates. Where a model version is specified in a deployment, the deployment will stop working on the deprecation date of that model version.

Implement one of the following model upgrade options:

-   **Auto Upgrade:** Create a new generative AI configuration and deployment or patch a deployment with a new configuration, specifying `modelVersion` `latest`. When a new `modelVersion` is supported by SAP AI Core, existing generative AI deployments will automatically use the latest version of the given model.

-   **Manual Upgrade:** Create a new generative AI configuation with your chosen replacement `modelVersion` and use it to patch your deployment. This model version will be used in generative AI deployments irrespective of updates to the models supported by SAP AI Core.

    > ### Note:  
    > If `modelVersion` isn’t specified, it will be `latest` by default. To upgrade manually, you **must** specify a `modelVersion`.


