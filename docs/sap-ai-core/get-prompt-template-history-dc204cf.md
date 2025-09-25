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
> For CaaS users the resource-group-id is extracted automatically, and does not need to be provided in the headers.



## Procedure

Send a GET request to endpoint `{{apiurl}}/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history` and include the name, scenario, and version of your prompt template.

 > ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history" \
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

