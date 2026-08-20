<!-- loiobc8ceadd9e08423586994b1e30f0d117 -->

# Get a Prompt Template



<a name="loiobc8ceadd9e08423586994b1e30f0d117__prereq_nbg_w2q_fdc"/>

## Prerequisites

-   You have created a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md) and [Create a Prompt Template \(Declarative\)](create-a-prompt-template-declarative-815def5.md).




## Context

You can retrieve a prompt template by ID, or by the combination of name, scenario, and version.

Prompt templates can also be retrieved and consumed in orchestration. For more information, see [Templating](templating-88c5608.md).

> ### Note:  
> Retrieval by ID offers immutability; guaranteeing that the prompt template behind the ID will not change.
> 
> Retrieval by name, scenario, and version are not immutable, and the latest iteration of the prompt template is retrieved.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users, the resource-group-id is extracted automatically, and doesn't need to be provided in the headers.



## Procedure

Send a GET request to the endpoint `$AI_API_URL/v2/lm/promptTemplates`, and include the information for your chosen retrieval method.

> ### Sample Code:  
> ```
> curl -X GET "$AI_API_URL/v2/lm/promptTemplates?name=example-prompt-template&scenario=categorization&version=0.0.1" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

> ### Sample Code:  
> ```
> curl -X GET "$AI_API_URL/v2/lm/promptTemplates/{{promptTemplateId}}" \
> -Header "Authorization: Bearer <your_auth_token>"
> ```

<a name="concept_lxt_k2v_zjc"/>

<!-- concept\_lxt\_k2v\_zjc -->

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
> The following code retrieves the first page of 10 prompt templates:
> 
> ```
> curl -X GET "$AI_API_URL/v2/lm/promptTemplates?$top=10&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> 
> ```
> 
> The following code retrieves the second page of 10 prompt templates:
> 
> ```
> curl -X GET "$AI_API_URL/v2/lm/promptTemplates?$top=10&$skip=10" \
>   -Header "Authorization: Bearer <your_auth_token>"
> 
> ```
> 
> The following code combines filters with pagination:
> 
> ```
> curl -X GET "$AI_API_URL/v2/lm/promptTemplates?scenario=categorization&$top=20&$skip=0" \
>   -Header "Authorization: Bearer <your_auth_token>"
> ```

Example response with pagination \(second page of 10, total 25 templates\):

> ### Output Code:  
> ```
> HTTP/1.1 200 OK
> Link: <$AI_API_URL/v2/lm/promptTemplates?$top=10&$skip=20>; rel="next", <$AI_API_URL/v2/lm/promptTemplates?$top=10&$skip=0>; rel="prev"
> 
> {
>   "count": 25,
>   "resources": [
>     {
>       "id": "8y02-ha9x-92b1-4255",
>       "name": "example-prompt-template",
>       "version": "0.0.1",
>       "scenario": "categorization",
>       "managedBy": "imperative",
>       "isVersionHead": true,
>       "creationTimestamp": "2021-09-29T14:00:00Z"
>     }
>   ]
> }
> ```

