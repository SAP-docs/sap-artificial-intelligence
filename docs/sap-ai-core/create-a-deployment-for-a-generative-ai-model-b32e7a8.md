<!-- loiob32e7a85f9e143c1924f31533ee81697 -->

# Create a Deployment for a Generative AI Model





<a name="loiob32e7a85f9e143c1924f31533ee81697__prereq_nzn_mdw_tyb"/>

## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](service-plans-c7244c6.md) and [Upgrade a Service Plan](upgrade-a-service-plan-924f892.md).



<a name="loiob32e7a85f9e143c1924f31533ee81697__context_ll5_4jw_tyb"/>

## Context

You make a model available for use by creating a deployment. You can do so one time for each model and model version. The model deployment includes the `modelName` and `version` of the model you want to access. After the deployment is complete, you have a `deploymentUrl`, which can be used across your organization to access the model version.

You can view the available models and their details by sending a GET request to the endpoint `{{apiurl}}/v2/lm/scenarios/foundation-models/models` 

<a name="concept_aw2_z2r_khc"/>

<!-- concept\_aw2\_z2r\_khc -->

## Choose a Model

Decide which LLM you want to deploy and note the following information:

-   Executable ID

-   Model name

-   Model version

    > ### Note:  
    > -   Instead of specifying a model version, using “latest” will use the latest version of the model available in SAP AI Core.
    > 
    > -   Where the model version is not listed, it is not applicable.


```
curl --location '$AI_API_URL/v2/lm/scenarios/foundation-models/models' \
--header 'AI-Resource-Group: default' \
--header 'Authorization: Bearer $AUTH_TOKEN'

```

> ### Output Code:  
> ```
> {
>   "count": 41,
>   "resources": [
>     {
>       "accessType": "Remote",
>       "allowedScenarios": [
>         {
>           "executableId": "azure-openai",
>           "scenarioId": "foundation-models"
>         },
>         {
>           "executableId": "orchestration",
>           "scenarioId": "orchestration"
>         }
>       ],
>       "description": "OpenAI GPT-4o engineered for speed and efficiency, supporting text, images and audio using Chat Completions API",
>       "displayName": "GPT-4o",
>       "executableId": "azure-openai",
>       "model": "gpt-4o",
>       "provider": "OpenAI",
>       "versions": [
>         {
>           "capabilities": [
>             "text-generation",
>             "image-recognition"
>           ],
>           "contextLength": 128000,
>           "cost": [
>             {
>               "inputCost": "0.00312"
>             },
>             {
>               "outputCost": "0.0092"
>             }
>           ],
>           "deprecated": false,
>           "inputTypes": [
>             "text",
>             "image",
>             "audio"
>           ],
>           "isLatest": false,
>           "metadata": [
>             {
>               "meanWinRate": "0.938"
>             },
>             {
>               "chatBotArenaScore": "1285"
>             },
>             {
>               "airBenchRefusalRate": "0.528"
>             }
>           ],
>           "name": "2024-05-13",
>           "retirementDate": "",
>           "streamingSupported": true
>         }, ...
> 
>     ]
> }
> ```

The output contains the following parameters, which are needed to create a configuration:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

count

</td>
<td valign="top">

Number of models available description

</td>
</tr>
<tr>
<td valign="top">

description

</td>
<td valign="top">

Description for model

</td>
</tr>
<tr>
<td valign="top">

executableId

</td>
<td valign="top">

Executable under which the model is available, required at the time of creating Deployment configuration model

</td>
</tr>
<tr>
<td valign="top">

model

</td>
<td valign="top">

Required as modelName at the time of creating Deployment configuration versions

</td>
</tr>
<tr>
<td valign="top">

versions

</td>
<td valign="top">

List of available model versions for given model

</td>
</tr>
<tr>
<td valign="top">

versions.name

</td>
<td valign="top">

Optional value to provide as modelVersion at the time of creating Deployment Configuration

</td>
</tr>
<tr>
<td valign="top">

versions.isLatest

</td>
<td valign="top">

Suggests if the modelVersion is latest. See Model Lifecycle for more information

</td>
</tr>
</table>

**For more information about available models, including conversion rates for tokens, rate limits and deprecation dates, see SAP Note [3437766](https://me.sap.com/notes/3437766).**



## Check Scenario

Check that you have access to the scenario containing generative AI by sending a GET request to `{{apiurl}}/v2/lm/scenarios`.

> ### Note:  
> You must use the same resource group for all of your generative AI activities. To use a different resource group, these steps must be repeated for each resource group.For more information, see [Manage Resource Groups](manage-resource-groups-8aae6cb.md).

```
curl --location '{{apiurl}}/v2/lm/scenarios' \
--header 'AI-Resource-Group: default' \
--header "Authorization: Bearer $AUTH_TOKEN"
```



### Step Result

The scenarios listed contain a scenario with the id `foundation-models`.

<a name="concept_xkc_32j_mhc"/>

<!-- concept\_xkc\_32j\_mhc -->

### Create a Deployment



<a name="concept_xkc_32j_mhc__section_xxd_bdj_mhc"/>

## Create a Configuration

Create a configuration by sending a POST request to the endpoint `{{apiurl}}/v2/lm/configurations`.

Include details of the model to which you want to provide access by passing in the following parameters:

-   `name` is your free choice of identifier.

-   `executableId`, `modelName`, and `modelVersion` are provided in SAP Note [3437766](https://me.sap.com/notes/3437766).

-   `scenarioId` must be `foundation-models`.

-   `versionId` is your own version reference.


> ### Sample Code:  
> ```
> curl --location '$AI_API_URL/v2/lm/configurations' \
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

**Step Result**

You receive a unique `configurationId` in the response.



## Create a deployment

Create a deployment by sending a POST request to the endpoint `{{apiurl}}/v2/lm/deployments`.

Include the `configurationId` from the previous step in your request.

> ### Sample Code:  
> ```
> curl --location '$AI_API_URL/v2/lm/deployments' \
> --header 'AI-Resource-Group: default' \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $AUTH_TOKEN" \
> --data '{
>  "configurationId": "yourConfigurationId"
> }'
> ```

<a name="concept_xtz_52j_mhc"/>

<!-- concept\_xtz\_52j\_mhc -->

## Next Steps



## Get Your Deployment ID

Retrieve the details of your deployment by sending a GET request to the endpoint`{{apiurl}}/v2/lm/deployments`.

```
curl --location '$AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID' \
--header 'AI-Resource-Group: default' \
--header "Authorization: Bearer $AUTH_TOKEN"
```

When the deployment is running, the model can be accessed using the `deploymentUrl` provided in the response. For more information, see [Consume Models](consume-models-bf0373b.md).

<a name="concept_fn1_2qy_szb"/>

<!-- concept\_fn1\_2qy\_szb -->

## Model Lifecycle

Model versions have deprecation dates. Where a model version is specified in a deployment, the deployment stops working on the deprecation date of that model version.

Implement one of the following model upgrade options:

-   **Auto Upgrade:** Create a new generative AI configuration and deployment or patch a deployment with a new configuration, specifying `modelVersion` `latest`. When a new `modelVersion` is supported by SAP AI Core, existing generative AI deployments will automatically use the latest version of the given model.

-   **Manual Upgrade:** Create a new generative AI configuration with your chosen replacement `modelVersion` and use it to patch your deployment. This model version is used in generative AI deployments irrespective of updates to the models supported by SAP AI Core.

    > ### Note:  
    > If `modelVersion` isn’t specified, it will be `latest` by default. To upgrade manually, you **must** specify a `modelVersion`.


