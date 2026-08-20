<!-- loioe8310f5318564eb588edd6a481f3f78b -->

# Get Orchestration Configs



## Prerequisites

You have created an orchestration config. For more information, see [Create an Orchestration Config \(Imperative\)](create-an-orchestration-config-imperative-2f27317.md)and [Create an Orchestration Config \(Declarative\)](create-an-orchestration-config-declarative-508e66f.md).



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
>       "managed_by": "declarative",
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



## Pagination

The list endpoint supports pagination using the `$top` and `$skip` query parameters. This is useful when you have a large number of prompt templates and want to retrieve them in pages.

> ### Note:  
> If the result set is too large and no pagination parameters are supplied, the API returns a `413 Payload Too Large` error. Use `$top` and `$skip` to paginate through the results.

The following parameters are supported:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default

</th>
<th valign="top">

Range

</th>
</tr>
<tr>
<td valign="top">

`$top`

</td>
<td valign="top">

Number of results to return per page

</td>
<td valign="top">

Full result set

</td>
<td valign="top">

1–500

</td>
</tr>
<tr>
<td valign="top">

`$skip`

</td>
<td valign="top">

Number of results to skip before returning the page

</td>
<td valign="top">

0

</td>
<td valign="top">

≥ 0

</td>
</tr>
</table>

The response includes a `Link` header with navigation links when more pages are available:

-   `rel=next` — URL for the next page of results.
-   `rel=prev` — URL for the previous page of results \(when applicable\).

The `count` field in the response body always reflects the total number of matching prompt templates \(not just the current page\).

> ### Sample Code:  
> The following code retrieves the first page of 10 orchestration configs:
> 
> ```
> curl -X GET "$AI_API_URL/v2/registry/v2/orchestrationConfigs?$top=10&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> 
> ```
> 
> The following code retrieves the second page of 10 orchestration configs:
> 
> ```
> curl -X GET "$AI_API_URL/v2/registry/v2/orchestrationConfigs?$top=10&$skip=10" \
>   -Header "Authorization: Bearer <your_auth_token>"
> 
> ```
> 
> The following code combines filters with pagination:
> 
> ```
> curl -X GET "$AI_API_URL/v2/registry/v2/orchestrationConfigs?scenario=scenario=customer-support&$top=20&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

Example response with pagination \(second page of 10, total 25 configs\):

> ### Output Code:  
> ```
> HTTP/1.1 200 OK
> Link: <$AI_API_URL/v2/registry/v2/orchestrationConfigs?$top=10&$skip=20>; rel="next", <$AI_API_URL/v2/registry/v2/orchestrationConfigs?$top=10&$skip=0>; rel="prev"
> 
> {
>   "count": 25,
>   "resources": [
>     {
>       "id": "<orchestrationConfigId>",
>       "name": "example-orchestration-config",
>       "version": "0.0.1",
>       "scenario": "customer-support",
>       "creation_timestamp": "2024-08-18T14:50:17.157000",
>       "managed_by": "imperative",
>       "is_version_head": true
>     }
>   ]
> }
> ```

