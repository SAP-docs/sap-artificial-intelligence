<!-- loiodc204cfa3dab48a18102192b342600bc -->

# Get Prompt Template History



## Context

You can list the history of edits to prompt templates, for imperatively managed prompt templates only.



## Procedure

Send a GET request to endpoint `{{apiurl}}/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history` and include the name, scenario, and version of your prompt template.

 > ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/lm/scenarios/{{scenarioId}}/promptTemplates/{{promptTemplateName}}/versions/{{versionId}}/history" \
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
>         "additionalFields": {
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

