<!-- loioe8310f5318564eb588edd6a481f3f78b -->

# Get Orchestration Configs



## Prerequisites

You have created an orchestration config. For more information, see [Create an Orchestration Config](create-an-orchestration-config-2f27317.md).



## Context

You can list all orchestration configs or retrieve a specific orchestration config by ID, or by the combination of name, scenario, and version.

Orchestration configs can also be retrieved and consumed in orchestration completion requests. For more information, see [Use an Orchestration Config in LLM Orchestration](use-an-orchestration-config-in-llm-orchestration-97e4cd2.md).

> ### Note:  
> Retrieval by ID offers immutability; guaranteeing that the orchestration config behind the ID will not change.
> 
> Retrieval by name, scenario, and version are not immutable, and the latest iteration of the orchestration config is retrieved.
> 
> Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/registry/v2/orchestrationConfigs`, and include the information for your chosen retrieval method.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core



### List All Orchestration Configs

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/registry/v2/orchestrationConfigs" \
>   -H "Authorization: Bearer <your_auth_token>"
> ```



### Get by Name, Scenario, and Version

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/registry/v2/orchestrationConfigs?name=example-orchestration-config&scenario=customer-support&version=0.0.1" \
>   -H "Authorization: Bearer <your_auth_token>"
> ```



### Get by ID

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/registry/v2/orchestrationConfigs/{{orchestrationConfigId}}" \
> -H "Authorization: Bearer <your_auth_token>"
> ```

> ### Tip:  
> Use the `resolve_template_ref=true` query parameter to resolve template references and include the full template definition in the response.



## Results

> ### Output Code:  
> ```
> {
>   "count": 3,
>   "resources": [
>     {
>       "id": "<orchestrationConfigId1>",
>       "name": "example-orchestration-config",
>       "version": "0.0.1",
>       "scenario": "customer-support",
>       "creation_timestamp": "2024-08-18T14:50:17.157000",
>       "managed_by": "imperative",
>       "is_version_head": true
>     },
>     {
>       "id": "<orchestrationConfigId2>",
>       "name": "another-orchestration-config",
>       "version": "1.0.0",
>       "scenario": "data-analysis",
>       "creation_timestamp": "2024-08-19T10:30:45.123000",
>       "managed_by": "imperative",
>       "is_version_head": true
>     }
>   ]
> }
> ```

