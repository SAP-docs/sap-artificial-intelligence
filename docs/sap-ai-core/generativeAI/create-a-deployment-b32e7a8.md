<!-- loiob32e7a85f9e143c1924f31533ee81697 -->

# Create a Deployment



## Prerequisites

-   You have an SAP AI Core service instance and service key. For more information, see [SAP AI Core Initial Setup Documentation](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/38c4599432d74c1d94e70f7c955a717d.html?locale=en-US&state=PRODUCTION&version=CLOUD).
-   You’re using the `extended` service plan. For more information, see [Service Plans](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/c7244c6a7e3b4ffc928a2564c216e7c7.html "The SAP AI Core service plan you choose determines pricing, conditions of use, resources, available services, and hosts.") :arrow_upper_right: and [Update a Service Plan](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/924f892e67b7443fbb4476b3e81959b2.html "Update your SAP AI Core service instance from the free plan to a standard or extended plan while keeping your data and models.") :arrow_upper_right:.
-   You've chosen the model that you want to make a deployment for. For more information, see [Choose a Model](choose-a-model-0ba2f0e.md).



## Context

You make a model available for use by creating a deployment. You can do so one time for each model and model version. The model deployment includes the `modelName` and `version` of the model you want to access. After the deployment is complete, you have a `deploymentUrl`, which can be used across your organization to access the model version.

Deployments for accessing models are made using the `foundation-models` scenario.

You can view the available models and their details by sending a GET request to the endpoint `{{apiurl}}/v2/lm/scenarios/foundation-models/models` 



## Check Scenario

Check that you have access to the scenario containing generative AI by sending a GET request to `{{apiurl}}/v2/lm/scenarios`.

> ### Note:  
> You must use the same resource group for all of your generative AI activities. To use a different resource group, these steps must be repeated for each resource group.For more information, see [Manage Resource Groups](https://help.sap.com/viewer/2d6c5984063c40a59eda62f4a9135bee/CLOUD/en-US/8aae6cbe2c0e4290954b8f61b4b355b7.html "A resource group is a unique dedicated namespace or workspace environment, where users can create or add configurations, executions, deployments, and artifacts. They are used for running training jobs or model servers.") :arrow_upper_right:.

```
curl --location '{{apiurl}}/v2/lm/scenarios' \
--header 'AI-Resource-Group: default' \
--header "Authorization: Bearer $AUTH_TOKEN"
```



### Step Result

The scenarios listed contain a scenario with the id `foundation-models`.



<a name="loiob32e7a85f9e143c1924f31533ee81697__section_xxd_bdj_mhc"/>

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



## Create a Deployment

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



## Get the Deployment URL

Retrieve the details of your deployment by sending a GET request to the endpoint `{{apiurl}}/v2/lm/deployments`.

```
curl --location '$AI_API_URL/v2/lm/deployments/$DEPLOYMENT_ID' \
--header 'AI-Resource-Group: default' \
--header "Authorization: Bearer $AUTH_TOKEN"
```

When the deployment is running, the model can be accessed using the `deploymentUrl` provided in the response. For more information, see [Consume Models](consume-models-bf0373b.md).

