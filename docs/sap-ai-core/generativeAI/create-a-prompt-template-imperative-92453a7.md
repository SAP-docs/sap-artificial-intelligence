<!-- loio92453a70576046cbbf3c2550a7a93191 -->

# Create a Prompt Template \(Imperative\)



## Context

> ### Recommendation:  
> The imperative API supports full CRUD operations and is recommended for refining prompt templates in design-time use cases. Iterations are tracked and can be viewed in the history endpoint.

You can create a reusable prompt for a specific use case, including placeholders that are filled later.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users, the resource-group-id is extracted automatically, and doesn't need to be provided in the headers.

> ### Note:  
> CaaS users only have write access to prompt templates on a resource-group level.



## Procedure

Create a prompt template by sending a POST request to endpoint <code><code>{{apiurl}}/v2/lm/promptTemplates</code></code>.

> ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/lm/promptTemplates"\
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --data '{
>     "name": "example-prompt-template",
>     "version": "0.0.1",
>     "scenario": "categorization",
>     "spec": {
>       "template": [
>         {
>           "role": "system",
>           "content": "You classify input text into the two following categories: {{?categories}}"
>         },
>         {
>           "role": "user",
>           "content": "{{?inputExample}}"
>         }
>       ],
>       "defaults": {
>         "categories": "Finance, Tech, Sports"
>       },
>       "additional_fields": {
>         "modelParams": {
>           "temperature": 0.7,
>           "max_tokens": 100
>         },
>         "modelGroup": "chat"
>       }
>     }
>   }'
> ```

-   The `defaults` and `additional_fields` fields are optional.

-   The `additional_fields` field is unstructured and can be used to store metadata or configuration objects.


> ### Output Code:  
> ```
> {
>   "id": "9y02-ha9x-92b1-4255",
>   "name": "example-prompt-template",
>   "versionId": "0.0.1",
>   "message": "Prompt created successfully."
> }
> ```



<a name="loio92453a70576046cbbf3c2550a7a93191__postreq_dg1_hb3_hdc"/>

## Next Steps

You can iterate over the prompt template and make changes to it.

You can save your changes as a new version. The latest iteration is always the head version and is marked with `isVersionHead: true`.

> ### Tip:  
> You'll need to update the version number when you want to create a new version, and the version entry must be compliant with semantic versioning \(SemVer\).

You can check the change history for the template. For more information, see [Get Prompt Template History](get-prompt-template-history-dc204cf.md).

