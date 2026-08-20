<!-- loio743e913924a54fbd84198b3bcb695898 -->

# Get Orchestration Config History



## Context

You can list the history of edits to orchestration configs for imperatively managed configurations.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a GET request to endpoint `{{apiurl}}/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs/{{orchestrationConfigName}}/versions/{{versionId}}/history` and include the name, scenario, and version of your orchestration config.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/registry/v2/scenarios/{{scenarioId}}/orchestrationConfigs/{{orchestrationConfigName}}/versions/{{versionId}}/history" \
>   -H "Authorization: Bearer <your_auth_token>"
> ```

> ### Output Code:  
> ```
> {
>   "count": 5,
>   "resources": [
>     {
>       "id": "<orchestrationConfigId>",
>       "name": "example-orchestration-config",
>       "version": "0.0.1",
>       "scenario": "customer-support",
>       "managed_by": "imperative",
>       "is_version_head": true,
>       "creation_timestamp": "2021-09-29T14:00:00Z",
>       "spec": {
>         "modules": {
>           "prompt_templating": {
>             "prompt": {
>               "template_ref": {
>                 "id": "<promptTemplateId>"
>               }
>             },
>             "model": {
>               "name": "<model>",
>               "params": {
>                 "temperature": 0.7,
>                 "max_tokens": 500
>               }
>             }
>           }
>         }
>       }
>     }
>   ]
> }
> ```



## Pagination

The history endpoint supports pagination using the `$top` and `$skip` query parameters.

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
> The following code retrieves the first page of 5 history entries:
> 
> ```
> curl -X GET "$AI_API_URL/v2/registry/v2/scenarios/$scenario/orchestrationConfigs/$name/versions/$version/history?$top=5&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```
> 
> The following code retrieves the next page of 5 history entries:
> 
> ```
> curl -X GET "$AI_API_URL/v2/registry/v2/scenarios/$scenario/orchestrationConfigs/$name/versions/$version/history?$top=5&$skip=5" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

