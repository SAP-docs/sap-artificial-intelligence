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
>       "id": "f47ac10b-58cc-4372-a567-0e02b2c3d479",
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
>                 "id": "a460d210-df38-4867-9535-7a556701a4b0"
>               }
>             },
>             "model": {
>               "name": "gpt-4o-mini",
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

