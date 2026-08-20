<!-- loiodc204cfa3dab48a18102192b342600bc -->

# Get Prompt Template History



## Context

You can list the history of edits to prompt templates, for imperatively managed prompt templates only.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users, the resource-group-id is extracted automatically, and doesn't need to be provided in the headers.



## Procedure

Send a GET request to endpoint `$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history` and include the name, scenario, and version of your prompt template.

> ### Sample Code:  
> ```
> curl -X GET "$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

> ### Output Code:  
> ```
> {
>   "count": 10,
>   "resources": [
>     {
>       "id": "8y02-ha9x-92b1-4255",
>       "name": "example-prompt-template",
>       "version": "0.0.1",
>       "scenario": "categorization",
>       "managedBy": "imperative",
>       "isVersionHead": true,
>       "creationTimestamp": "2021-09-29T14:00:00Z",
>       "spec": {
>         "template": [
>           {
>             "role": "system",
>             "content": "You classify input text into the two following categories: {{?categories}}"
>           },
>           {
>             "role": "user",
>             "content": "{{?inputExample}}"
>           }
>         ],
>         "defaults": {
>           "categories": "Finance, Tech, Sports"
>         },
>         "additional_fields": {
>           "modelParams": {
>             "temperature": 0.7,
>             "max_tokens": 100
>           },
>           "modelGroup": "chat"
>         }
>       }
>     }
>   ]
> }
> ```

> ### Note:  
> Responses for requests on a resource-group level, will include a `resourceGroupId` field, holding the hashed `resource-group-id`, instead of the `managedBy` field.



### Pagination

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
> curl -X GET "$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history?$top=5&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```
> 
> The following code retrieves the next page of 5 history entries:
> 
> ```
> curl -X GET "$AI_API_URL/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history?$top=5&$skip=5" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

