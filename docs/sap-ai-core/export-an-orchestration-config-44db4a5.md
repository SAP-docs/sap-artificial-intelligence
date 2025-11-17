<!-- loio44db4a55e6ee40788cf0f7235f4242e2 -->

# Export an Orchestration Config



## Prerequisites

You have created an orchestration config. For more information, see [Create an Orchestration Config](create-an-orchestration-config-2f27317.md).



## Context

You can export an orchestration config as a single file export in YAML format.

Orchestration configs are handled at the tenant level and do not require resource group headers.



## Procedure

Send a GET request to the endpoint `{{apiurl}}/v2/registry/v2/orchestrationConfigs/{{orchestrationConfigId}}/export`, and include the name of your file in the output parameter.

Set the following in the headers:

-   `AI_API_URL`: the base URL of your SAP AI Core environment.
-   `{{access_token}}`: Your access token for SAP AI Core

> ### Sample Code:  
> ```
> curl -X GET "{{apiurl}}/v2/registry/v2/orchestrationConfigs/{{orchestrationConfigId}}/export" \
> -H "Authorization: Bearer <your_auth_token>" \
> --output "exported_orchestration_config.yaml"
> 
> ```

> ### Output Code:  
> ```
> name: example-orchestration-config
> version: 0.0.1
> scenario: customer-support
> spec:
>   modules:
>     prompt_templating:
>       prompt:
>         template_ref:
>           id: <promptTemplateId>
>       model:
>         name: <model>
>         params:
>           temperature: 0.7
>           max_tokens: 500
> 
> ```

