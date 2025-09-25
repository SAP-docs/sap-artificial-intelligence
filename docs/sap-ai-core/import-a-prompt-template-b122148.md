<!-- loiob122148a6c7c4d5584cb6a1955744071 -->

# Import a Prompt Template



<a name="loiob122148a6c7c4d5584cb6a1955744071__prereq_ovx_knq_fdc"/>

## Prerequisites

-   You have created and exported a prompt template. For more information, see [Create a Prompt Template \(Imperative\)](create-a-prompt-template-imperative-92453a7.md) and [Export a Prompt Template](export-a-prompt-template-3acef9b.md).




## Context

You can import a declarative prompt template as a single file export in yaml format.

By default, prompt templates are handled on the main-tenant level. To handle them on resource-group level, add the `AI-Resource-Group-Scope` and `AI-Resource-Group` headers to your requests. For example:

```

--header 'AI-Resource-Group-Scope: true'
--header 'AI-Resource-Group: <resource group>'
```

> ### Note:  
> For CaaS users the resource-group-id is extracted automatically, and does not need to be provided in the headers.

> ### Note:  
> CaaS users only have write access to prompt templates on a resource-group level.



## Procedure

Send a POST request to the endpoint `{{apiurl}}/v2/lm/promptTemplates/import`, and include the name of your file in the `file` parameter.

 > ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/lm/promptTemplates/import" \
>      -Header "Authorization: Bearer <your_auth_token>" \
>      -Header "Content-Type: multipart/form-data" \
>      -File "file=@/path/to/your/file.yaml"
> ```

 > ### Output Code:  
> ```
> {
>   "message": "Prompt <prompt-name> for version <version-number> imported successfully.",
>   "resource": {
>     "name": "example-prompt-template",
>     "version": "0.0.1",
>     "scenario": "job-description",
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
>   }
> }
> ```

