<!-- loio716d4c38e3054c93a9d481b51cc66298 -->

# AI API Overview

The AI API lets you manage your AI assets \(such as training scripts, data, models, and model servers\) across multiple runtimes.

Argo workflows and serving templates, as well as their execution and deployment, are managed using the SAP AI Core implementation of the AI API. In SAP AI Core, the Argo workflow and serving templates are mapped under the concept of `Executable`. For the mapping mechanism to work, the Argo workflows and serving templates require certain attributes in the metadata section of the `YAML` file. These attributes are shared by both template types.

SAP AI Core provides additional APIs that are runtime-specific. These are available in the AI Core API specification, which is an extension of the AI API specification.



**Related Information**  


[AI Core API](https://api.sap.com/package/SAPAICore/rest)

[AI API](https://help.sap.com/doc/2cefe221fddf410aab23dce890b5c603/CLOUD/en-US/index.html)

<a name="loiodbacc5fee07c4e43a656f5d1203654c7"/>

<!-- loiodbacc5fee07c4e43a656f5d1203654c7 -->

## AI API Runtime Implementations

The AI API specification is a general specification for the lifecycle management of machine learning artifacts. SAP AI Core is one specific runtime implementation of the AI API specification. It is also possible to provide other runtime implementations of the AI API specification, independent of SAP AI Core. This section describes the necessary boundary conditions and implementation requirements.

The benefit of using AI API is that clients can integrate with all AI API-enabled runtime implementations. For example, SAP AI Launchpad can interact with custom runtime implementations as long as the same APIs are provided. Intelligent Scenario Lifecycle Management can also integrate with AI API-enabled runtimes. The SAP AI SDK Base \(Python\) can also be used \(for more information, see [sap-ai-sdk-core](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/499309d6e371419fb7a88b7d68c20a31.html#%0Asap-ai-core-sdk)\).



<a name="loiodbacc5fee07c4e43a656f5d1203654c7__section_x2r_k5t_4sb"/>

## AI API Specification

The AI API specification comprises the following parts:

-   A main specification

-   Extensions:

    -   Analytics extension

    -   Resource group extension

    -   Dataset management extension
        -   Metrics extension




> ### Recommendation:  
> Implement at least the main specification, and then implement the extension specifications based on your use case.



<a name="loiodbacc5fee07c4e43a656f5d1203654c7__section_rd2_nyp_nsb"/>

## AI API Runtime Capabilities Endpoint

`Meta API` is part of the AI API specification \(endpoint `/lm/meta`\). The implementation must return a configuration response that specifies the capabilities of the AI API runtime implementation.

`Meta API` allows AI API clients to query the capabilities of an AI API implementation so that they can select which commands or user interfaces are available. For example, some AI API runtimes may offer executions but not deployments. They may also offer logs for executions and not for deployments. As an example, if a client of SAP AI Core such as SAP AI Launchpad queries the `Meta API` endpoint of SAP AI Core, the response will be for example:

```
json
						
{
	"aiApi": {
		"capabilities": {
			"logs": {
				"deployments": true,
				"executions": true
			},
			"multitenant": true,
			"shareable": true,
			"staticDeployments": true,
			"timeToLiveDeployments": true,
			"userDeployments": true,
			"userExecutions": true
			"executionSchedules": true
		},
		"limits": {
			"deployments": {
				"maxRunningCount": -1
			},
			"executions": {
				"maxRunningCount": -1
			},
			"minimumFrequencyHour": 1,
			"timeToLiveDeployments": {
					"minimum": "10m",
					"maximum": -1
			}
		},
		"version": "2.18.0"
	},
	"extensions": {
		"analytics": {
			"version": "1.0.0"
		},
		"metrics": {
			"capabilities": {
				"extendedResults": true
			},
			"version": "1.0.0"
		},
		"resourceGroups": {
			"version": "1.2.0"
		}
	},
	"runtimeApiVersion": "2.21.0",
	"runtimeIdentifier": "aicore"
}
```

SAP AI Launchpad and other clients can then react accordingly and hide the deployments on the user interface for this runtime implementation of AI API.

Capabilities include the following:


<table>
<tr>
<th valign="top">

Capability

</th>
<th valign="top">

When true, allows users to:

</th>
</tr>
<tr>
<td valign="top">

`logs.executions`

</td>
<td valign="top">

View logs for an execution

</td>
</tr>
<tr>
<td valign="top">

`logs.deployments`

</td>
<td valign="top">

View logs for a deployment

</td>
</tr>
<tr>
<td valign="top">

`multitenant`

</td>
<td valign="top">

Use SAP AI Launchpad as a main tenant user \(supports resource groups\)

</td>
</tr>
<tr>
<td valign="top">

`shareable`

</td>
<td valign="top">

Clients can share one instance

</td>
</tr>
<tr>
<td valign="top">

`staticDeployments`

</td>
<td valign="top">

Static, always running endpoints for inference are available without the user having to start a deployment

</td>
</tr>
<tr>
<td valign="top">

`userDeployments`

</td>
<td valign="top">

Stop, update, or delete a deployment

</td>
</tr>
<tr>
<td valign="top">

`userExecutions`

</td>
<td valign="top">

Stop or delete an execution

</td>
</tr>
<tr>
<td valign="top">

`timeToLiveDeployments`

</td>
<td valign="top">

The runtime engine allows defining the time until a deployment is automatically deleted

</td>
</tr>
<tr>
<td valign="top">

`analytics`

</td>
<td valign="top">

Review summary information for all tenants

</td>
</tr>
<tr>
<td valign="top">

`bulkUpdates`

</td>
<td valign="top">

Stop or delete up to 100 executions or deployments at once

</td>
</tr>
<tr>
<td valign="top">

`executionSchedules`

</td>
<td valign="top">

Create schedules

</td>
</tr>
</table>

Limits include the following:


<table>
<tr>
<th valign="top">

Limit

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

`deployments.maxRunningCount`

</td>
<td valign="top">

Limits the number of running concurrent deployments in a resource group, if any

</td>
</tr>
<tr>
<td valign="top">

`executions.maxRunningCount`

</td>
<td valign="top">

Limits the number of running concurrent executions in a resource group, if any

</td>
</tr>
<tr>
<td valign="top">

`timeToLiveDeployments.minimum`

</td>
<td valign="top">

The minimum possible value for the ttl parameter in a deployment, if supported

</td>
</tr>
<tr>
<td valign="top">

`timeToLiveDeployments.maximum`

</td>
<td valign="top">

The maximum possible value for the ttl parameter in a deployment, if supported

</td>
</tr>
<tr>
<td valign="top">

`minimumFrequencyHour`

</td>
<td valign="top">

The minimum possible value for schedule of an execution, if supported

</td>
</tr>
</table>

In addition to the general AI API specification, there is also a number of extensions that cover additional use cases. These might not be implemented in all runtime engines.

The extensions are:


<table>
<tr>
<th valign="top">

Extension

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

`analytics`

</td>
<td valign="top">

The analytics extension contains endpoints for fetching analytical information of a resource group or tenant

</td>
</tr>
<tr>
<td valign="top">

`metrics`

</td>
<td valign="top">

The metrics extension contains endpoints for writing to and reading from metrics endpoints, to store and retrieve metrics generated during executions

</td>
</tr>
<tr>
<td valign="top">

`resourceGroups`

</td>
<td valign="top">

The resource group extension contains endpoints for managing resource groups

</td>
</tr>
<tr>
<td valign="top">

`dataset`

</td>
<td valign="top">

The dataset extension contains endpoints for uploading and downloading files

</td>
</tr>
</table>

**Related Information**  


[Serving Templates](serving-templates-20a8667.md "You use serving templates to manage your serving instances at the level of the main tenant. Serving templates define how a model is to be deployed.")

[Workflow Templates](workflow-templates-83523ab.md "Here, you'll find a basic workflow example template. Feel free to adjust it to suit your workflow needs.")

[AI API Specification](https://help.sap.com/doc/2cefe221fddf410aab23dce890b5c603/CLOUD/en-US/index.html)

[Custom Runtime Capabilities Using the Meta API](https://help.sap.com/docs/AI_LAUNCHPAD/92d77f26188e4582897b9106b9cb72e0/ac3d92b6fe604ede99a382be5b1008e5.html)

[Analytics Extension](https://help.sap.com/doc/3674682b79464e3686ee296ade22d012/CLOUD/en-US/analytics_extension.html)

[Resource Groups Extension](https://help.sap.com/doc/ee5bbd9141b341029ad1767d26294dde/CLOUD/en-US/resource_groups_extension.html)

[Intelligent Scenario Lifecycle Management](https://help.sap.com/viewer/8308e6d301d54584a33cd04a9861bc52/latest/en-US/436151b128614f0e84024015136043d3.html)

