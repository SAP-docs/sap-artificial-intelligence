<!-- loio2f273172fc1d468d833760ac4302ad21 -->

# Create an Orchestration Config



## Context

The imperative API supports full CRUD operations and is recommended for both design-time and runtime orchestration configuration use cases. Iterations are tracked and can be viewed in the history endpoint.

You can create a reusable orchestration configuration for a specific use case, including module configurations for filtering, masking, grounding, and prompt templating.

Orchestration configs are handled at the tenant level and do not require resource group headers.

Orchestration configs can reference existing prompt templates in two ways:

-   By template ID for immutable references
-   By name, scenario, and version for flexible references that can point to the latest version



## Procedure

Create an orchestration config by sending a POST request to endpoint `{{apiurl}}/v2/registry/v2/orchestrationConfigs`.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core

The following examples show only the `prompt_templating` module for simplicity. Orchestration configs can include all supported modules such as `filtering`, `masking`, `grounding`, and `translation` in addition to `prompt_templating`.

> ### Note:  
> Use template references by ID when you need immutable references that won't change. Use references by name, scenario, and version when you want flexibility to update the underlying template while keeping the same orchestration config.



### Example With Inline Prompt Template

> ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/registry/v2/orchestrationConfigs" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --data '{
>     "name": "example-orchestration-config",
>     "version": "0.0.1",
>     "scenario": "customer-support",
>     "spec": {
>       "modules": {
>         "prompt_templating": {
>           "prompt": {
>             "template": [
>               {
>                 "role": "system",
>                 "content": "You are a helpful customer support assistant."
>               },
>               {
>                 "role": "user",
>                 "content": "{{?userQuery}}"
>               }
>             ],
>             "defaults": {
>               "userQuery": "How can I help you today?"
>             }
>           },
>           "model": {
>             "name": "gpt-4o-mini",
>             "params": {
>               "temperature": 0.7,
>               "max_tokens": 500
>             }
>           }
>         }
>       }
>     }
>   }'
> ```



### Example With Prompt Template Reference by ID

> ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/registry/v2/orchestrationConfigs" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --data '{
>     "name": "example-orchestration-config",
>     "version": "0.0.1",
>     "scenario": "customer-support",
>     "spec": {
>       "modules": {
>         "prompt_templating": {
>           "prompt": {
>             "template_ref": {
>               "id": "a460d210-df38-4867-9535-7a556701a4b0"
>             }
>           },
>           "model": {
>             "name": "gpt-4o-mini",
>             "params": {
>               "temperature": 0.7,
>               "max_tokens": 500
>             }
>           }
>         }
>       }
>     }
>   }'
> ```



### Example With Prompt Template Reference by ID

> ### Sample Code:  
> ```
> curl -X POST "{{apiurl}}/v2/registry/v2/orchestrationConfigs" \
> --header 'Content-Type: application/json' \
> --header "Authorization: Bearer $TOKEN" \
> --data '{
>     "name": "example-orchestration-config",
>     "version": "0.0.1",
>     "scenario": "customer-support",
>     "spec": {
>       "modules": {
>         "prompt_templating": {
>           "prompt": {
>             "template_ref": {
>               "scenario": "categorization",
>               "name": "example-prompt-template",
>               "version": "0.0.1"
>             }
>           },
>           "model": {
>             "name": "gpt-4o-mini",
>             "params": {
>               "temperature": 0.7,
>               "max_tokens": 500
>             }
>           }
>         }
>       }
>     }
>   }'
> ```



## Results

You will receive an output JSON containing details about your configuration, including an ID and success message.

> ### Output Code:  
> ```
> {
>   "id": "f47ac10b-58cc-4372-a567-0e02b2c3d479",
>   "name": "example-orchestration-config",
>   "version": "0.0.1",
>   "scenario": "customer-support",
>   "message": "Orchestration config created successfully."
> }
> ```



## Next Steps

You can iterate over the orchestration config and make changes to it.

You can save your changes as a new version. To create a new version, update the version number. Your entry must be compliant with semantic versioning \(SemVer\). The latest iteration is always the head version and is marked with `is_version_head: true`.

You can check the change history for the config. For more information, see [Get Orchestration Configs](get-orchestration-configs-e8310f5.md).

